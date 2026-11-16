# HW4 — Short Answers

Answer each question in 2–3 sentences.

## 1. Rolling-update safety
Why does the Deployment use `maxUnavailable: 0`, and what would change if it were `maxUnavailable: 1`?

maxUnavailable sets the number of Kubernetes pods before an update is made. Since we have three pods, and the max that can unavailable is 3, that means that 3 pods must be up and running before an update. If it was set at 1, that would mean that only 2 of the 3 pods needed to be up and running which could lead to reduced capacity or dropped requests.

## 2. Health probes
Why do the liveness/readiness probes target `/health` instead of `/predict`?

/health makes sure the API is running and healthy before running the predcition. If the prediciton has an error, it could be becuase of mulitple things including an unhealthy API. But for the /predict to run the API has to be healthy and we can easily and quickly check that part by running /health.

## 3. Autoscaling under load
Your HPA scales at 40% CPU up to 8 pods. If request volume doubled, what would you expect to happen — and what happens once it reaches the maximum?

The HPA tries to cap CPU usage at 40% or less. It does this by adding up to 8 Kubernetes pods. If the request doubles, I would expect more pods to be added. Once it reaches 8 pods, the CPU usage might go above 40%.