# Xeon E5-2680 v4 Dedicated Server: Plans, Specs & Pricing

Plenty of cores, plenty of memory and a sensible price. That is the whole case for a dual Xeon E5-2680 v4 server. Two 14 core processors give you 28 cores and 56 threads, with 128 GB of DDR4 RAM, on a machine that only you use.

The YouStable [Xeon E5-2680 v4 dedicated server](https://www.youstable.com/dedicated-servers/intel/xeon-e5-2680-v4) comes in two plans with the same processors and the same memory. The real decision is the storage: a simple 2 TB NVMe, or eight 3.84 TB SAS SSDs for large, durable storage. This guide helps you make that choice, shows you the specs, gives you an honest view of whether this older chip is still worth buying, and walks you through ordering step by step.

## NVMe or SAS SSD: Choose Your Plan

Both servers are dual processor machines with 128 GB of DDR4, unmetered bandwidth and a 1 Gbps uplink (10 Gbps on request). Setup is free on both.

| | Plan with NVMe | Plan with SAS SSDs |
|---|---|---|
| Processors | 2 x Xeon E5-2680 v4 | 2 x Xeon E5-2680 v4 |
| Cores / Threads | 28 Cores / 56 Threads | 28 Cores / 56 Threads |
| Speed | 2.4 GHz base, up to 3.3 GHz turbo | 2.4 GHz base, up to 3.3 GHz turbo |
| RAM | 128 GB DDR4 | 128 GB DDR4 |
| Storage | 2 TB NVMe | 8 x 3.84 TB SAS SSD |
| Raw storage | 2 TB | 30.72 TB |
| Bandwidth | Unmetered | Unmetered |
| Price | **$229/month** | **$319/month** |
| Regular price | $286/month | $399/month |
| Saving | 20%, which is $57 a month | 20%, which is $80 a month |

The NVMe plan costs about $8.18 per core per month, and the SAS SSD plan about $11.39. Moving up to the SAS plan costs $90 more a month, and for that you get roughly 28.7 TB of extra raw space, which works out to about $3.13 per TB.

Both plans are listed as USA plans on the YouStable Intel server page, so confirm the location on the order page and think about how close it is to your users.

### Which One Do You Need?

| Your Situation | Better Fit |
|---|---|
| Most workloads: databases, build servers, dev and test labs | NVMe plan |
| You want speed and simplicity with a single fast drive | NVMe plan |
| Large datasets, media libraries and shared file stores | SAS SSD plan |
| VM farms that need lots of durable storage | SAS SSD plan |
| You want RAID for redundancy | SAS SSD plan, since it has eight drives to arrange |

The SAS SSDs are enterprise drives, built for steady writes and endurance, which suits busy VM farms and databases.

### Planning RAID on the SAS SSD Plan

With eight drives, you decide how to arrange them. In a semi-managed server, the RAID layout and storage planning are yours.

| Layout | Usable Space | What You Get |
|---|---|---|
| RAID 0 | 30.72 TB | Maximum space and speed, no protection if a drive fails |
| RAID 5 | 26.88 TB | One drive can fail without data loss |
| RAID 6 | 23.04 TB | Two drives can fail without data loss |
| RAID 10 | 15.36 TB | Fast, with a drive able to fail in each mirrored pair |

These are standard storage calculations. The options available depend on how the server is configured, so talk to the YouStable team before you order. And remember that RAID is not a backup, so keep a copy of important data somewhere else.

### A Note on the NVMe Plan

The 2 TB NVMe plan has a single drive. That makes it fast and simple, but if the drive fails, your data is gone unless you have a backup. Set up regular backups to a separate location from day one.

## Xeon E5-2680 v4 Specifications

Each processor is a 14 core Broadwell-EP chip, and your server carries two of them. These are Intel's published figures.

| Spec | Intel Xeon E5-2680 v4 |
|---|---|
| Cores / Threads (per CPU) | 14 Cores / 28 Threads |
| In This Server (2 CPUs) | 28 Cores / 56 Threads |
| Base Clock | 2.4 GHz |
| Max Turbo Clock | Up to 3.3 GHz |
| Architecture | Broadwell-EP, 14nm |
| L3 Cache (per CPU) | 35 MB |
| Default TDP (per CPU) | 120W |
| Socket | LGA 2011-3, dual socket |
| Memory Support | DDR4-2400, 4 channels per CPU |
| Max Memory (per CPU) | Up to 1.5 TB |
| Processor Interconnect | 2 x QPI links at 9.6 GT/s |
| PCIe | PCIe 3.0, 40 lanes per CPU |
| Instruction Extensions | AVX2 and AES-NI |
| Virtualization | Intel VT-x and VT-d |

### What Two Sockets Mean for You

Your 128 GB of RAM is shared between two processors, so each one has about 64 GB of memory that it reaches fastest. This design is called NUMA, and hypervisors and databases handle it well. For best results, try to keep a VM or process on one socket.

You can see your layout with these commands:

```bash
lscpu
nproc
```

The `nproc` command should show 56, which is the number of threads your build tools can use. For example, `make -j56` runs 56 compile jobs at once.

The platform supports far more memory than 128 GB, and if you need extra, ask the team about a custom build. Storage is different. It depends on the 8 bay chassis, so ask support before planning any additions.

## Is a 2016 Chip Still Worth It?

Honest answer: it depends on your workload. Broadwell cores are slower than a modern EPYC core. What you are buying is cores and memory capacity at a low price, which is exactly what throughput work needs.

| Good Fit | Not the Best Fit |
|---|---|
| Virtualization with many VMs | A single threaded application |
| Databases with many connections | Work that needs the fastest possible single core |
| Build farms and parallel jobs | Software that cannot use many threads |
| Consolidating several old servers | Small sites that will never use 28 cores |

### Xeon E5-2680 v4 vs 2 x Xeon Platinum 8173M vs Xeon E3-1230v3

The dual E5-2680 v4 sits between a small single socket Xeon and the larger Platinum pair. It is the budget way to get 28 cores.

| Spec | 2 x Xeon E5-2680 v4 | 2 x Xeon Platinum 8173M | Xeon E3-1230v3 |
|---|---|---|---|
| Cores / Threads | 28 / 56 | 56 / 112 | 4 / 8 |
| Base / Boost Clock | 2.4 GHz / Up to 3.3 GHz | 2.0 GHz / Up to 3.5 GHz | 3.3 GHz / Up to 3.7 GHz |
| Architecture | Broadwell-EP, 14nm | Skylake-SP, 14nm | Haswell, 22nm |
| Sockets | 2 | 2 | 1 |
| Best for | Budget virtualization, databases and build farms | Dense virtualization and large databases | Small sites, dev and staging |

On price, the Platinum pair is $499 a month, with 512 GB of RAM and two 7.68 TB SAS SSDs. At $8.91 per core, it costs a little more per core than the E5-2680 v4 NVMe plan, but it brings four times the memory. If you need less memory and want the lowest price per core, the E5-2680 v4 is the leaner pick. If you want faster individual cores, a modern chip is a better fit.

## What to Run on a Xeon E5-2680 v4 Server

Anything that grows with core count and memory.

| Workload | Why It Fits |
|---|---|
| Virtualization host | KVM or Proxmox guests on 56 threads, each with real cores and memory |
| Database servers | MySQL, PostgreSQL or SQL Server with 128 GB of RAM to cache data |
| CI/CD build farms | Many build and test runners in parallel |
| Docker and Kubernetes | A container platform on one node with plenty of cores |
| Hosting platforms | A portfolio of client sites or reseller accounts behind a control panel |
| Rendering and transcoding | FFmpeg encodes or Blender frames spread across 56 threads |
| ERP and business suites | Business software and its database together, without sharing a CPU |
| Dataset and media storage | The SAS SSD plan as a large, fast store for datasets, media and shared files |
| Dev and test labs | Large stacks on hardware that mirrors production |

### A Sample Way to Split the Server

This is only an example to help you picture the capacity. Your real split will depend on your workloads.

| Environment | vCPUs | RAM |
|---|---|---|
| Host and hypervisor | Shared | 8 GB |
| 8 general purpose VMs | 4 each | 8 GB each |
| 2 database VMs | 8 each | 24 GB each |
| Spare for growth | | 8 GB |

That is 48 vCPUs and the full 128 GB, on a machine with 56 threads.

## Semi-Managed Support and What Is Included

A dual processor server rewards clear roles. The machine and its network are YouStable's responsibility, and the software running on it is yours.

| YouStable Looks After | You Look After |
|---|---|
| Network, uplink and DDoS protection | Operating system updates and security hardening |
| Hardware health across both CPUs, the memory and every drive | Your hypervisor, databases and applications |
| Power, cooling and the data center | Backups of your own data |
| Monitoring and help with serious issues | RAID layout and storage planning |
| Free server setup | |

Chat, ticket and email support run 24/7, and phone support is open Monday to Saturday, 9:00 AM to 5:30 PM IST. If you would rather click than type, you can add cPanel or Plesk.

| Included | Details |
|---|---|
| Setup | Free |
| Migration | Free. YouStable engineers move your existing sites at no charge |
| Root access | Full root or administrator access |
| Security | Firewall and DDoS protection |
| Uptime | 99.95% SLA, which allows roughly 22 minutes of downtime in a month |
| Network | Unmetered traffic on a 1 Gbps uplink, 10 Gbps on request |
| Data centers | Tier III/IV |
| Hardware | 100% hardware replacement guarantee |
| Operating systems | AlmaLinux, Rocky Linux, Ubuntu, Debian and Windows Server, with custom ISO uploads supported |

### Optional Add-ons

Every add-on is optional and billed only when you enable it.

| Add-on | Starting Price |
|---|---|
| Softaculous (1 click installer, 400+ apps) | $2.50 |
| DirectAdmin | $5.00 |
| Additional IPv4 | $5.00 |
| Imunify360 (firewall, malware scanner, intrusion detection) | $10.00 |
| LiteSpeed web server | $10.00 |
| Plesk | $16.99 |
| Premium Support | $18.86 |
| Windows Server OS with RDP | $25.00 |
| cPanel & WHM | $69.99 |

## How to Order and Set Up Your Server (Step by Step)

1. **Check the fit.** Make sure your workload can use many threads. If it cannot, a smaller server will cost far less.
2. **Choose your storage.** Pick the 2 TB NVMe plan or the 8 x 3.84 TB SAS SSD plan, using the tables above.
3. **Plan your RAID and backups.** If you choose the SAS SSD plan, decide your RAID layout. For either plan, decide where your backups will live.
4. **Open the plan page.** Go to the [Xeon E5-2680 v4 dedicated server page](https://www.youstable.com/dedicated-servers/intel/xeon-e5-2680-v4) and review both plans.
5. **Click Configure Now** on the plan you want.
6. **Choose your operating system.** AlmaLinux, Rocky Linux, Ubuntu, Debian and Windows Server are supported, and you can bring your own ISO, such as the hypervisor you prefer. You can reinstall any time from your control panel.
7. **Add what you need.** Pick a control panel, Imunify360, LiteSpeed, extra IPv4 addresses or Premium Support if they suit your project.
8. **Create your account and pay.** Sign up on [YouStable](https://www.youstable.com/) and complete your order. There is no setup fee.
9. **Secure the server.** The firewall and DDoS protection are included. Add your own hardening: update the system, close unused ports and use key based SSH login.
10. **Set up your platform.** Create your RAID layout if needed, then install your hypervisor, database or build tools.
11. **Migrate your workloads.** YouStable engineers move your existing sites at no charge. Run your workloads on the new server while the old one is still live, and test everything.
12. **Go live.** Lower your DNS TTL a day or two before, then point your domain to the new server. Check your backups work before you rely on them.

Need a domain for a new project? You can register it from the same [YouStable](https://www.youstable.com/) account and manage hosting and domain together.

## FAQs

### What is a Xeon E5-2680 v4 dedicated server?

It is a dual socket bare metal server with two Intel Xeon E5-2680 v4 processors. Each has 14 cores and 28 threads, so you get 28 cores and 56 threads on one machine that nobody else shares.

### How much does it cost?

The plan with 2 TB NVMe is $229 per month, and the plan with eight 3.84 TB SAS SSDs is $319 per month. Setup is free on both.

### What does semi-managed mean?

YouStable looks after the network, hardware, power and cooling, and helps when something serious goes wrong. You run the operating system, RAID, software and backups.

### Is the Xeon E5-2680 v4 still worth it in 2026?

Yes, for the right jobs. Its cores are slower than a modern EPYC core, but you get a lot of cores and memory for the money, which suits virtualization, databases and build farms.

### How many cores does the dual Xeon E5-2680 v4 server have?

28 cores and 56 threads in total, from two 14 core, 28 thread processors.

### Can I add more RAM or drives?

The platform supports far more memory than 128 GB, so ask the team about a custom build. Storage depends on the 8 bay chassis, so check with support before you plan it.

### Is migration free?

Yes. YouStable engineers move your existing sites at no charge, and you only pay for the hardware.

## Conclusion

The dual Xeon E5-2680 v4 is the budget way to get 28 cores and 56 threads on a server that only you use. Choose the 2 TB NVMe plan at $229 a month for most workloads, or the SAS SSD plan at $319 a month when you need about 30 TB of durable storage, and you get unmetered traffic, a firewall, DDoS protection and engineers on call 24/7.

Ready to deploy? Check both plans on the [Xeon E5-2680 v4 dedicated server page](https://www.youstable.com/dedicated-servers/intel/xeon-e5-2680-v4), or visit [YouStable](https://www.youstable.com/) if you also need hosting or a domain name for your project.
