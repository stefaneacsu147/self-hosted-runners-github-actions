# Self hosted runners in Kubernetes

If you would like to deploy GitHub Actions to your **Kubernetes** (_GKE, EKS, etc_) you can use th following
configuration.

At the moment the example is setup at organization level but you can also set it up to be bound at repository level.

## Steps

Build first your image, in my case I am using Google Container Registry to build my Docker image.

After the image was built be sure you changed in the `deployment.yaml` to the correct image and also you can switch the
tag from latest and bound it to a specific version.

Run `kubectl apply -f deployment.yaml`. Check afterwards using `kubectl get deployment -n github-actions` if the
deployment was succesfully deployed.

Afterwards, you can go ahead and use `kubectl get po -n github-actions` and check the pods to see if they are healthy.

If you want to check the logs and that the runners are actually on and listening for jobs,
use `kubectl logs "name of the pod" -n github actions` and inspect one of the pods for errors or if it's active.