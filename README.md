# QRES-L1-blockchain-node

# IXIOS Migration

This repository documents the process of migrating an IXIOS L1 validator node from a cloud-based Virtual Private Server to a dedicated server, with a focus on performance optimization, security hardening, and reliability improvements.

---
## Server Specifications

### Original Environment
- **Platform**: Cloud VPS
- **CPU**: 2 vCPU
- **RAM**: 4GB

### New Environment
- **CPU**: Intel Core i9-13900 (24 cores / 32 threads @ 2 GHz)
- **RAM**: 64GB ECC DDR5
- **Storage**: 2 x 1.92TB NVMe SSD Datacenter Edition (RAID configuration)
- **Operating System**: Ubuntu 24.04 LTS (Noble)
---

## Migration Process

### 1. Server Provisioning
- Generated dedicated SSH key for server authentication
- Provisioned dedicated server with secure SSH key authentication
- Configured remote access and initial security settings

### 2. System Configuration
- Installed Ubuntu 24.04 LTS
- Initially configured RAID 1 for redundancy
- Later optimized to RAID 0 for maximum storage capacity while maintaining RAID 1 for boot partition
- Configured partitioning scheme for optimal performance

### 3. Validator Migration
- Securely transferred validator keys from original server
- Installed IXIOS validator toolkit on new server
- Configured validator software with existing credentials
- Monitored blockchain synchronization process

### 4. Security Hardening
- Implemented key-based SSH authentication only
- Configured UFW firewall with restrictive rules
- Installed and configured Fail2ban for brute force protection
- Deployed Tailscale for secure overlay networking
- Created auto-reconnect service for networking resilience

### 5. Monitoring Setup
- Configured container-based monitoring stack
- Implemented automatic recovery procedures
- Created status checking scripts

## Security Features
- SSH key-only authentication
- Fail2ban with progressive ban times
- UFW firewall with minimal exposed services
- Secure overlay network with Tailscale
- Automated recovery systems

## Lessons & Incident Response
- Documented hardware reset procedures
- Created recovery playbooks for common scenarios
- Implemented automated reconnection services
- Identified and mitigated network-level vulnerabilities

## Maintenance
Standard maintenance commands:
```bash
# Recovery procedure (after reset)
podman start grafana loki prometheus node-exporter promtail
```

## Technologies Used
- IXIOS AetherSeed validator toolkit v2.1.0rc1
- IXIOS L1 v1.1.0rc3
- Ubuntu 24.04 LTS
- Podman containers
- Tailscale VPN
- Software RAID
- UFW & Fail2ban
