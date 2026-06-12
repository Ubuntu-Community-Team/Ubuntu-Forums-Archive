---
title: "How to configure HPC cluster with MAAS and run KVM on top"
date: 2023-03-19
forum: General Help
---

### Post by atif2 on 2023-03-19
Hi,

I have two IBM SR550 Xeon Sliver 2100 CPU with 64Gb RAM each. I would like to configure a HPC cluster with MAAS on Ubuntu 20.04 and want to run KVM solution for the virtualization. My goal is to operate KVM on distributed infrastructure. Is it possible to add or remove bare metal hardware in cluster if require without down time?

I need community guidance to accomplish the task for demo purposes or kindly suggest alternate solution

Thanks

---

### Post by TheFu on 2023-03-19
I can't recall anyone ever posting anything about MAAS in these forums.  Just thought you should know.  The forums are 90% desktop users and 10% server people, if that.

BTW, there is a separate sub-forum for MAAS and JUJU stuff.  Hopefully, a moderator will move this thread there.  I know that MAAS wants to control DNS and DHCP for all the client systems.

If you want clustering of KVM systems, I'd look at **proxmox**.  Perhaps MAAS does that too. IDK.

---

### Post by MAFoElffen on 2023-03-19
<< The section for MASS is "Cloud and Juju": [https://ubuntuforums.org/forumdisplay.php?f=392](https://ubuntuforums.org/forumdisplay.php?f=392) >>

Though, you might note that a lot of those started threads there go unanswered...

---

### Post by MAFoElffen on 2023-03-19
My thoughts on this... Which is just my own personal opinion, based on my own experiences with the pieces of what you brought up. TheFU has experience with datacenters, and Snap App's. I'm sure he might add to this.

Start with Ubuntu Server LTS version 22.04.2. I see no reason to start with 20.04.

Install your servers in an Ubuntu Cluster...
RE: [https://www.particleincell.com/2020/ubuntu-linux-cluster/](https://www.particleincell.com/2020/ubuntu-linux-cluster/)
That tutorial is for 18.04, but the basics are still the same.

Install KVM.
RE: [https://linuxhint.com/install-kvm-ubuntu-22-04/](https://linuxhint.com/install-kvm-ubuntu-22-04/)

Create VM Server templates...
RE: [https://www.tecmint.com/create-kvm-virtual-machine-template/](https://www.tecmint.com/create-kvm-virtual-machine-template/)

Start playing with it and testing what you can do...

The switching over on fail-over on bare-metal, running, they appear as one with whatever they are running, whether than be an SQL database or KVM... Clustering of VM's inside KVM is another perspective in another layer. You can do that on KVM without Proxmox. Proxmox adds another layer on top of KVM. Personally I like the hands-on control I have now, without adding that extra layer to managing things from a web-based interface. (Proxmox or Console) It didn't make sense for me to add that layer between what I was doing. I don't have a team working for me, that I have to make that easier for 'them'.

Beyond the marketing hype: MAAS is just another discussion altogether. What I saw in it when I tested it when it rolled out was that it's use for physical, bare-metal deployments from templates, and treating them as if they "were" virtual machines in the deployments of them. In it's purpose and use, it is a datacenter tool. Machine life-cycle management and deployments. (My VM lifecyles are short-lived, because my infrastructure is for testing, debugging and resolving replicated problems.)

*I tried out MAAS, O-Virt, Console, just doing ansible/terraform... I am still looking for what works best for me in what I do.*

I use the same methodology in how i deploy VM's. I tried it to see if it was something I wanted to use in the deployment of VM's. I could not see it adding any value to what I was already doing. It was easy to deploy machines, but I already had made my own VM templates that I created on my own... So I couldn't see adding another layer into my infrastructure, where I was not gaining anything more from it. Then when they changed the "how it was implemented" to being a Snap App, it became less desirable for me. I just clone, and spin up servers from my templates that I have sanitized, then make the id config changes to make them unique.

You only have two physical machines that you are deploying as a cluster. One logical machine, made up of two nodes... MAAS would be on another machine, that you would be deploying that one logical machine... Hmmm... Seems like extra work and overkill right? Just pointing out that observation.

If you are doing this, as a demo, and example of what the possibilities of doing something at scale (managing and deploying thousands), then that is another discussion, where it would well be worth it.

Just my thoughts on this.

---

