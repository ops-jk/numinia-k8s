# Numinia Kubernetes Naming Conventions

This document outlines the standardized naming conventions for Kubernetes resources within the Numinia organization.

## General Structure

All resources follow this general pattern:
```
hyperfy2-numinia-<service>-<resource-type>[-<subtype>]
```

Where:
- `hyperfy2-`: Platform prefix (always lowercase)
- `numinia-`: Organization prefix (always lowercase)
- `<service>`: Service name (e.g., city-of-mesa, age-of-ai)
- `<resource-type>`: Kubernetes resource type (e.g., deployment, service)
- `[-<subtype>]`: Optional subtype for specific cases

## Resource Types

### Workload Resources
- Deployments: `hyperfy2-numinia-<service>-deployment`
- StatefulSets: `hyperfy2-numinia-<service>-statefulset`
- Jobs: `hyperfy2-numinia-<service>-job`
- CronJobs: `hyperfy2-numinia-<service>-cronjob`

### Network Resources
- Services: `hyperfy2-numinia-<service>-service`
- Ingress/Routes: `hyperfy2-numinia-<service>-route`
- Middlewares: `hyperfy2-numinia-<service>-middleware`

### Configuration Resources
- ConfigMaps: `hyperfy2-numinia-<service>-config`
- Secrets: `hyperfy2-numinia-<service>-secret`
- ServiceAccounts: `hyperfy2-numinia-<service>-sa`

### Storage Resources
- PersistentVolumeClaims: `hyperfy2-numinia-<service>-pvc`
- Volumes: `hyperfy2-numinia-<service>-volume`
- Storage Claims: `hyperfy2-numinia-<service>-storage`

## Labels

Standard labels for all resources:
```yaml
labels:
  app: hyperfy2-numinia-<service>
  environment: prod
  component: <specific-component>
```

## Environment Variables

Environment variables should follow:
- Use uppercase
- Use service prefix
- Format: `<SERVICE>_<VARIABLE>`
- Example: `CITY_OF_MESA_PORT`, `AGE_OF_AI_DOMAIN`

## Examples

### Deployment
```yaml
metadata:
  name: hyperfy2-numinia-city-of-mesa-deployment
  labels:
    app: hyperfy2-numinia-city-of-mesa
    environment: prod
```

### Service
```yaml
metadata:
  name: hyperfy2-numinia-city-of-mesa-service
  labels:
    app: hyperfy2-numinia-city-of-mesa
    environment: prod
```

## Best Practices

1. Always use lowercase for resource names
2. Use hyphens (-) as separators in resource names
3. Keep names concise but descriptive
4. Maintain consistency across all services
5. Include both platform (hyperfy2-) and organization (numinia-) prefixes in all resource names

## Namespace Convention

All resources should be in the `numinia` namespace unless there's a specific requirement for isolation. 