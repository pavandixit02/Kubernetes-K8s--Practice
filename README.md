# ☸️ Kubernetes Hands-on Lab | Learn K8s by Doing

<p align="center">
  <strong>A Practical Journey into Kubernetes, Container Orchestration & DevOps</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kubernetes-Learning-326CE5?logo=kubernetes&logoColor=white" alt="Kubernetes Learning" />
  <img src="https://img.shields.io/badge/Platform-Ubuntu-E95420?logo=ubuntu&logoColor=white" alt="Ubuntu" />
  <img src="https://img.shields.io/badge/Infrastructure-YAML-CB171E?logo=yaml&logoColor=white" alt="YAML" />
  <img src="https://img.shields.io/badge/Focus-Cloud%20%26%20DevOps-2496ED?logo=docker&logoColor=white" alt="Cloud and DevOps" />
  <img src="https://img.shields.io/badge/Approach-Hands--On-success" alt="Hands-on Learning" />
</p>

## 📌 About This Repository

Welcome to my **Kubernetes Hands-on Practice Lab**!

This repository documents my practical learning journey with Kubernetes (K8s), the open-source platform for automating the deployment, scaling, and management of containerized applications.

Instead of learning concepts only through theory, I am exploring Kubernetes through YAML manifests, command-line operations, application deployment exercises, configuration management, networking, and persistent storage.

Every practical is organized into dedicated directories, with configuration files and screenshots documenting my work.

**My objective:** Build a strong practical foundation in Kubernetes and apply it to real-world Cloud and DevOps engineering workflows.

---

## 🎯 Learning Goals

- Understand Kubernetes architecture and core components.
- Create, inspect, and manage Pods.
- Organize workloads using Namespaces.
- Configure CPU and memory requests and limits.
- Deploy applications and expose them through Services.
- Manage application configuration using ConfigMaps and Secrets.
- Understand persistent storage using PVs, PVCs, and volumes.
- Develop confidence with `kubectl` and declarative YAML.
- Document practical exercises for future reference.
- Progress toward Helm, monitoring, security, and production-oriented Kubernetes practices.

## 🗂️ Repository Structure

```text
Practice-K8s/
│
├── first-practical/
│   ├── command-1.png
│   ├── command-2.png
│   └── pod.yaml
│
├── namespace-resoureslimit/
│   ├── execute-command-1.png
│   ├── execute-command-2.png
│   ├── namespace.yaml
│   └── pod-limits.yaml
│
├── react-app-deploy/
│   ├── execute-commands.png
│   ├── run-in-vs_code.png
│   └── run-localhost.png
│
├── second-service/
│   ├── command-1.png
│   ├── command-2.png
│   ├── deployment.yaml
│   ├── pod.yaml
│   ├── service-loadbalancer.yaml
│   ├── service-nodeport.yaml
│   └── tab-output.png
│
├── secret-configmap/
│   ├── configmap.yaml
│   ├── execute-commands.png
│   ├── pod-env.yaml
│   └── secret.yaml
│
├── third-volume/
│   ├── execute-command.png
│   ├── pod-with-volume.yaml
│   ├── pvc.yaml
│   └── pv.yaml
│
└── README.md
```

## 📚 Practical Learning Modules

### 01 — Kubernetes Pods

<details>
<summary><strong>Explore concepts, objectives and commands</strong></summary>

**Directory:** `first-practical/`

**Objective:** Understand the basic execution unit of Kubernetes and learn to create a Pod through a YAML manifest.

**Concepts**
- Pod fundamentals and container workloads.
- Declarative resource creation.
- YAML manifest structure.
- Pod status inspection and lifecycle management.

**Practice commands**

```bash
kubectl apply -f pod.yaml
kubectl get pods
kubectl get pods -o wide
kubectl describe pod <pod-name>
kubectl delete -f pod.yaml
```

**Expected learning outcome:** Understand how a Pod is defined, created, inspected, and deleted.

</details>

### 02 — Namespaces and Resource Management

<details>
<summary><strong>Explore isolation and CPU/memory limits</strong></summary>

**Directory:** `namespace-resoureslimit/`

**Objective:** Learn how to organize resources into Namespaces and configure container resource requirements.

**Concepts**
- Namespace-based resource organization.
- CPU and memory requests.
- CPU and memory limits.
- Inspecting workloads within a Namespace.

**Practice commands**

```bash
kubectl apply -f namespace.yaml
kubectl get namespaces
kubectl apply -f pod-limits.yaml
kubectl get pods -A
kubectl describe pod <pod-name> -n <namespace>
```

**Expected learning outcome:** Understand resource organization and how CPU/memory requests and limits affect container scheduling and execution.

</details>

### 03 — React Application Practice

<details>
<summary><strong>Explore application execution and deployment workflow</strong></summary>

**Directory:** `react-app-deploy/`

**Objective:** Document the React application workflow and its execution through the available screenshots.

**Topics**
- Application execution workflow.
- Localhost access and verification.
- Development environment observations.
- Potential next step: containerize the application and deploy it to Kubernetes.

**Documentation:** Review the screenshots in this directory to understand the recorded execution steps.

**Future enhancement:** Add the React source code, Dockerfile, Kubernetes Deployment and Service manifests if they are part of the intended Kubernetes deployment exercise.

</details>

### 04 — Deployments and Services

<details>
<summary><strong>Explore workload management and networking</strong></summary>

**Directory:** `second-service/`

**Objective:** Practice workload definitions and understand how Kubernetes Services provide network access to applications.

**Concepts**
- Pod and Deployment manifests.
- Service selectors and target ports.
- NodePort access.
- LoadBalancer Service configuration.
- Inspecting deployed resources.

**Practice commands**

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service-nodeport.yaml
kubectl get deployments
kubectl get pods -o wide
kubectl get services
kubectl describe service <service-name>
```

To test the LoadBalancer configuration, use:

```bash
kubectl apply -f service-loadbalancer.yaml
kubectl get svc
kubectl describe svc <service-name>
```

**Important:** A LoadBalancer Service needs a supported load-balancer implementation or environment. In local clusters, an external IP may remain pending until the appropriate setup is configured.

**Expected learning outcome:** Understand how workloads are exposed and how to investigate Service configuration.

</details>

### 05 — ConfigMaps and Secrets

<details>
<summary><strong>Explore application configuration and sensitive values</strong></summary>

**Directory:** `secret-configmap/`

**Objective:** Understand how configuration data and sensitive values can be provided to Kubernetes workloads.

**Concepts**
- ConfigMaps for non-sensitive configuration.
- Secrets for sensitive values.
- Environment variable references.
- Linking configuration resources to Pods.

**Practice commands**

```bash
kubectl apply -f configmap.yaml
kubectl apply -f secret.yaml
kubectl apply -f pod-env.yaml

kubectl get configmaps
kubectl get secrets
kubectl describe pod <pod-name>
```

**Security best practices**

- Never commit real credentials to a public repository.
- Do not treat Base64 encoding as encryption.
- Use appropriate access controls for Secrets.
- Consider encryption at rest and external secret-management solutions for production workloads.

**Expected learning outcome:** Understand the separation of application configuration from workload definitions.

</details>

### 06 — Persistent Storage: PV, PVC and Volumes

<details>
<summary><strong>Explore storage provisioning and persistence</strong></summary>

**Directory:** `third-volume/`

**Objective:** Learn how Kubernetes storage resources can provide persistent data storage beyond a container's lifecycle.

**Concepts**
- PersistentVolumes (PV).
- PersistentVolumeClaims (PVC).
- Pod volume mounts.
- Storage capacity and access modes.
- Storage binding and troubleshooting.

**Practice commands**

```bash
kubectl apply -f pv.yaml
kubectl get pv

kubectl apply -f pvc.yaml
kubectl get pvc

kubectl apply -f pod-with-volume.yaml
kubectl get pods
kubectl describe pvc <pvc-name>
```

**Troubleshooting commands**

```bash
kubectl get pv,pvc
kubectl describe pv <pv-name>
kubectl describe pod <pod-name>
kubectl get events --sort-by=.metadata.creationTimestamp
```

**Important:** PVC binding depends on storage class, capacity, access modes, and the available storage provisioner. Apply the manifests in the order appropriate to their configuration.

**Expected learning outcome:** Understand how storage resources are declared, claimed, mounted, and inspected.

</details>

---

## ⚙️ Prerequisites

Before running the practicals, prepare a working Kubernetes environment.

| Requirement | Purpose |
|---|---|
| Ubuntu or Linux | Practice environment |
| Kubernetes cluster | Run Kubernetes workloads |
| `kubectl` | Manage and inspect cluster resources |
| YAML fundamentals | Define Kubernetes resources |
| Basic Linux commands | Navigate files and troubleshoot |
| Container fundamentals | Understand application workloads |

A local cluster can be created with tools such as Minikube or kind. Choose a setup appropriate to your system.

### Verify your environment

```bash
kubectl version --client
kubectl cluster-info
kubectl get nodes
kubectl config current-context
```

If cluster commands fail, verify that the cluster is running and your current Kubernetes context is correct.

## 🚀 Getting Started

### 1. Open the repository

```bash
cd ~/Desktop/Practice-K8s
```

### 2. Review the available files

```bash
tree
find . -name '*.yaml' -o -name '*.yml'
```

### 3. Validate a manifest

```bash
kubectl apply --dry-run=client -f first-practical/pod.yaml
```

Client-side dry runs validate the manifest against client-side checks; they do not guarantee that the resource will work in the cluster.

### 4. Deploy a practical

```bash
kubectl apply -f first-practical/pod.yaml
```

### 5. Inspect the result

```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl get events --sort-by=.metadata.creationTimestamp
```

### 6. Clean up resources

```bash
kubectl delete -f first-practical/pod.yaml
```

**Note:** Follow the README instructions in each module and review its YAML files before applying resources. Replace placeholder names with the actual resource names defined in the manifests.

---

## 🧰 Essential `kubectl` Command Reference

| Task | Command |
|---|---|
| List Pods | `kubectl get pods` |
| List all Namespaces | `kubectl get namespaces` |
| List all Pods across Namespaces | `kubectl get pods -A` |
| List Deployments | `kubectl get deployments` |
| List Services | `kubectl get services` |
| Inspect a resource | `kubectl describe pod <pod-name>` |
| View container logs | `kubectl logs <pod-name>` |
| Execute a command in a container | `kubectl exec -it <pod-name> -- sh` |
| Apply a manifest | `kubectl apply -f <file.yaml>` |
| Delete a manifest's resources | `kubectl delete -f <file.yaml>` |
| Inspect recent events | `kubectl get events` |
| View active context | `kubectl config current-context` |

Some commands require appropriate permissions or a running workload. For example, `kubectl exec` requires a running Pod with a suitable container shell.

## 🔍 Troubleshooting Checklist

When a workload does not behave as expected, investigate systematically.

**Pod problems**
```bash
kubectl get pods -A
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

**Service connectivity**
```bash
kubectl get svc
kubectl get endpoints
kubectl describe svc <service-name>
```

**Storage problems**
```bash
kubectl get pv,pvc
kubectl describe pvc <pvc-name>
```

**Cluster events**
```bash
kubectl get events --sort-by=.metadata.creationTimestamp
```

Common issues include invalid YAML indentation, incorrect resource names, image pull failures, missing configuration, resource constraints, selector mismatches, and unavailable storage.

## 📈 Learning Progress Tracker

The checklist below represents my learning roadmap. I will mark topics complete after verifying the corresponding practical.

- [x] Create an initial Pod manifest.
- [x] Organize practical files and screenshots.
- [ ] Verify Pod creation and lifecycle commands.
- [ ] Validate Namespace and resource-limit behavior.
- [ ] Verify React application deployment to Kubernetes.
- [ ] Test Deployment and Service connectivity.
- [ ] Verify ConfigMap and Secret consumption.
- [ ] Test PV/PVC binding and persistent data behavior.
- [ ] Practice Kubernetes troubleshooting.
- [ ] Install and use Helm Charts.
- [ ] Explore probes, scaling, and rolling updates.
- [ ] Practice Ingress and access control.
- [ ] Add monitoring and observability.

**Progress tracking note:** The checked items indicate repository setup and the presence of initial practical artifacts, not independent verification that every exercise has been executed successfully.

## 🛣️ Next Steps: Kubernetes to DevOps

My planned learning path:

1. **Core Kubernetes:** Pods, Deployments, ReplicaSets and Namespaces.
2. **Networking:** ClusterIP, NodePort, LoadBalancer and Ingress.
3. **Configuration:** ConfigMaps, Secrets and environment variables.
4. **Storage:** Volumes, PVs, PVCs and StorageClasses.
5. **Application reliability:** Health probes, resource requests and limits.
6. **Scaling and releases:** Replica scaling and rolling updates.
7. **Helm:** Install, configure, upgrade and roll back Helm releases.
8. **Security:** RBAC, ServiceAccounts and least-privilege access.
9. **Observability:** Metrics, logs, Prometheus and Grafana.
10. **CI/CD:** Automate application builds and Kubernetes deployments.

## 📸 Screenshots and Practical Evidence

Each practical directory includes screenshots of selected commands, outputs, or application execution.

These screenshots help document the learning process and make it easier to revisit previous exercises. The YAML files provide the configuration artifacts used for the corresponding practicals.

## 👨‍💻 About Me

I am building my hands-on skills in **Cloud Computing, Linux, Kubernetes, and DevOps engineering** through consistent practice and technical documentation.

This repository is a living lab: I will continue adding practical examples, improving manifests, documenting errors, and exploring production-oriented concepts as my knowledge grows.

**My learning philosophy:** Learn the concept, implement it, verify the result, troubleshoot the failure, and document the solution.

## 🤝 Contributions and Feedback

Suggestions, corrections, and ideas for improving these practical exercises are welcome.

If you are also learning Kubernetes, feel free to explore the repository and use the examples as a reference. Always review manifests and adjust them to your own cluster before applying them.

## ⭐ Final Note

This repository reflects my ongoing journey toward becoming a **Cloud / DevOps Engineer**. Each practical is a step toward understanding how modern applications are deployed, configured, connected, and operated with Kubernetes.

**Keep learning. Keep building. Keep improving.**

---

<p align="center">
  <strong>Built with curiosity, documented through practice. ☸️</strong>
</p>
