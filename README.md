# VMware-Wintel
>1.How many roles and features are available in Windows Server?
2. Have you ever installed or configured a vCenter Server? If yes, how did you set it up?
3. What is the difference between LDAP, LDAPS, and Kerberos authentication?
4.. How can you list all installed Windows Server roles and features using PowerShell?
5. How do you configure networking on an ESXi host?
What challenges have you faced while patching ESXi hosts or Windows servers?
6. What is DHCP failover, and what are the available failover modes?
7. One of your Domain Controllers is offline — how would you handle this?
8. What is NIC teaming, and what load-balancing options does it provide?
9. Since you are doing Inplace upgrade , so assume After an in-place upgrade, some drives are missing — how do you attach disks from the old server?
10. A user is unable to log in to the domain — what checks would you perform?
11. What is the use of Active Directory Sites and Subnets?
12. What is DNS, and what’s the difference between A, CNAME, and PTR records?
13. What is the difference between NTFS permissions and Share permissions?
14. In VMware what is Standard and Distributed Switch
>1. What is Legacy BIOS and UEFI BIOS? Explain the differences.
2. How many partitions can we create on a Primary GPT disk?
3. Could you tell me what is the work of Boot Configuration Data (BCD)?
4.Have you configured RAID without using any third-party tool?
5.If I give you a server and ask you to create a virtual environment / 
6.Infrastructure for your Wintel team, how would you do it? What are the necessary components required?
8.How would you migrate an On-Prem server to Azure Cloud?
9.If a Domain Controller is down, what is the best way to recover it?
10.If PDC Emulator is down, what will happen?
11. How do you transfer FSMO roles using CLI commands? Can you list them out?
12.How many roles and features are available in Windows Server?
13. Have you ever installed or configured a vCenter Server? If yes, how did you set it up?
14. What is the difference between LDAP, LDAPS, and Kerberos authentication?
15.. How can you list all installed Windows Server roles and features using PowerShell?
16. What is DHCP failover, and what are the available failover modes?
17. One of your Domain Controllers is offline — how would you handle this?
18. What is NIC teaming, and what load-balancing options does it provide?
19. Since you are doing Inplace upgrade , so assume After an in-place upgrade, some drives are missing — how do you attach disks from the old server?
20. A user is unable to log in to the domain — what checks would you perform?
21. What is the use of Active Directory Sites and Subnets?
22. What is DNS, and what’s the difference between A, CNAME, and PTR records?
23. What is the difference between NTFS permissions and Share permissions?

    ## 5 production real time scenarios worked on wintel and vmware ##
    1. Critical application slowness caused by VMware CPU contention
       “A business critical application became slow during peak hours. I checked Windows CPU, memory, disk latency, services, and application logs, then compared those findings with vCenter performance metrics.

Windows CPU utilization alone did not explain the problem. I identified elevated CPU Ready alongside heavy host utilization, indicating that the VM was waiting for physical CPU resources.

After checking destination host capacity and vMotion compatibility, I migrated the VM to a less busy host under the approved incident procedure. I monitored performance and worked with the application team to validate response times.

Service performance recovered within [actual duration]. I documented the root cause and recommended capacity monitoring and a review of VM sizing.”
## 2. VMware datastore capacity incident caused by backup snapshots
 “I handled a datastore capacity alert that threatened multiple production VMs. I reviewed datastore utilization, recent vCenter tasks, snapshot growth, and backup job history.

I found that a failed backup workflow had left snapshots growing on an active VM. I coordinated with the backup team to resolve the failed job and checked for backup related locks.

Before consolidation, I assessed the required free space and arranged additional capacity through the storage team. I then consolidated the affected disks using supported vSphere operations and monitored storage latency and application availability.

After recovery, I verified datastore capacity, consolidation status, and the next backup cycle. I introduced snapshot age and size reporting to help identify similar failures earlier.”
Note : Technical point to remember: Insufficient datastore space and backup related file locks can prevent consolidation; never manually delete snapshot disk files to reclaim space.

## 3. Active Directory and DNS issue affecting user authentication
“Users at one office reported intermittent login failures and problems accessing domain resources. I established the affected scope and checked connectivity, DNS configuration, time synchronization, and domain controller event logs.

I used repadmin /replsummary, repadmin /showrepl, and dcdiag /test:dns to investigate domain controller health. The evidence showed that incorrect DNS settings on an affected domain controller were preventing reliable name resolution and replication.

Through the approved change process, I corrected the DNS configuration and verified the required records. I then confirmed that replication succeeded and tested authentication and Group Policy processing with affected users.

I documented the configuration issue and added DNS and replication health checks to the operational checklist.”
Note : Technical point to remember: DNS misconfiguration is a recognized cause of AD replication failures. Explain which diagnostic result identified the fault, rather than just listing commands.
## 4. Production application failed after Windows patching
“Following a scheduled Windows patching activity, a production application failed its health checks. I joined the incident bridge, confirmed the business impact, and reviewed the patch timeline, reboot status, Windows events, application logs, and service dependencies.

The logs showed that an application service had failed during startup because a required dependency was unavailable. After confirming the dependency was healthy, I started the services in the correct order and worked with the application team to test the complete user transaction.

We restored service within [actual duration]. I monitored the server for recurrence and documented the evidence behind the recovery.

I improved the patching runbook by adding dependency checks, service validation, and application owner sign off after reboot.”
Note : Recruiter value: This demonstrates controlled troubleshooting, incident communication, and validation of business service recovery.
## 5. Planned ESXi maintenance with application availability maintained
“I supported ESXi maintenance for a production VMware cluster. Before the change, I reviewed the approved upgrade path, hardware compatibility, backup status, cluster health, spare capacity, and VM migration restrictions.

I coordinated the maintenance window with application owners and migrated workloads from one host at a time. After confirming evacuation, I placed the host into maintenance mode, applied the approved update, and rebooted it.

Before returning it to service, I checked management connectivity, storage paths, networking, host health, and VM operation. I repeated the process only after each host passed validation.

The maintenance completed within [actual window], with [actual availability outcome]. I updated the change record with validation evidence and any follow up actions.”

