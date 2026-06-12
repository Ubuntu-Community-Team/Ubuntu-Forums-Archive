---
title: "Looking for help to monitor NAS mounting and trigger reboot or mount"
date: 2019-07-31
forum: General Help
---

### Post by spelunk68 on 2019-07-31
Hello all,
I can fumble my way around Ubuntu but I am still mostly a noob. I have deployed a couple of Unifi NVR systems and because of the myriad of issues running this on a windows machine with mongod I decided to run it on an OS native to Unifi video NVR. There is one issue I can not figure out and google searches are not reflecting my issue in its responses.
I have the Ubuntu server mounting a Synology disk station at /nas. If there is a power outage (which happens once in a while since the system is running on generators) the Ubuntu server boots up immediately but the Synology with its 112 TB iscsi takes a bit longer so if both are powered up at the same time the NAS does not mount as it is not present at the running of fstab (also mount -a does not mount it but a reboot after the synology is up does). I know there is some package or command that makes ubuntu wait for the mounts to be present to boot but that only addresses half of my issue. The other part is if the UPS on the Synology faults (this just happened) I am left in the same situation where I have now created another mount issue.
Is the a script anyone can help with, or maybe a package that checks mounted systems every say 5 minutes and if a mount is not present it reboots the system? I know rebooting is a little extreme but a mount going dark causes issues not only wth the mount being reinstated but also with the NVR software now starts acting funky and a reboot is the most complete way I have seen to reset to a working state.
The most important part of this system is that the recordings are being saved all of the time and viewing or using any other aspect of the Ubuntu server comes in second. I always need the NAS mounted and it is the most important aspect of this system as recovering recordings from multiple paths and also recovering recordings off a half full 112 TB drive never seems to succeed and I need to avoid it in the first place.
Or does this come down to a simple remount script if a frequent check of the mount status fails?
Any ideas?
Thank you.

---

### Post by TheFu on 2019-07-31
I know nothing about NVR.

Add _netdev to the mount options to delay mounting network storage. Doubt that will help, since it only delays until the Ubuntu network is up, not the extra time some other device might need on the LAN.

Also, if you use **autofs**, then the mount would only be attempted when specifically requested and you can automate that.  If the mount dies, autofs will mount it again at the next request.  Do not use "hard" as an option, since that will effectively lock up the client.

Reallly, the power problem needs to be fixed.  Having block devices disappear is asking for all sorts of problems, especially file system corruption.

I'm confused ... you're talking about iSCSI, but also talking about a mount, like it is NFS.  Huh?  Please clarify.  If a NAS supports NFS, you should always use that rather than other options.

---

### Post by spelunk68 on 2019-08-01
Thanks I will look into autofs. It was set up with iscsi for higher throughput over windows fs from when they were using windows then we switched the server to Ubuntu because of the mongod issues and the NAS's were already set up with a months worth of recordings on them. With the size of the volume and the way the Synology is handling the volume every NAS shows and treats it as a full volume even though when mounted the free space is there. This makes it  impossible to migrate a 112 TB volume to anything else currently implemented on site and the client can not loose their recordings. This is not something I normally do but I am trying to help clean it up.

---

### Post by dragonfly41 on 2019-08-01
This is a shot in the dark since I know absolutely nothing about the subject.
But intuitively an administrative tool [such as webmin]("https://community.ui.com/questions/Unifi-Video-NVR-Appliance-Add-Webmin-GUI-for-easy-Server-Administration/9bdd67a6-db1e-4ecb-b443-e3f620c0ae17") might be easier to use.
You can set various tasks to run through webmin GUI.
Or perhaps ansible to control your resources.
[Later edit] Found reference to CLI tool [here]("https://ubuntuforums.org/showthread.php?t=2344988&highlight=cli-companion"). It is "CLI companion".

---

### Post by TheFu on 2019-08-01
webmin should be avoided, IMHO.  The only place where it might be useful is when there is 1 senior Linux admin who can securely set it up for about 10 things, so jr admins can do something immediately, but tools like webmin tend to break and jr admins never learn to be proper admins with it.  That does you, them, and the company a disservice.  Admins should know how to perform all the tasks from a shell that tools like webmin provide.

Everywhere I've seen webmin deployed, it provided multiple new attack vectors and drastically reduced network security.

I use Ansible.  No sure how it would help at all here.  It would be easier to have a cron job run every 5 min to check for a specific file on the mount location. If that file doesn't exist ... do something.  I don't know what there is to be done, since I don't understand the relationship between the iSCSI and Ubuntu and some other system being used and the SAN device.  The terms haven't been used in a clear way.

---

### Post by dragonfly41 on 2019-08-01
> [COLOR=#000000]but tools like webmin tend to break and jr admins never learn to be proper admins with it.[/COLOR]

I do hugely respect the professional opinion of @TheFu and others who prefer CLI only.
But I'm a solo developer with eyes open and I understand the security risks if webmin is misused.
It need not always be open and the ability to add a repo of Custom Commands and modules is a plus for me.
Whatever happened to CLI-commander (if I remember the name correctly)?
But horses for courses.

[Later edit] Found reference to [CLI Companion here]("https://ubuntuforums.org/showthread.php?t=2344988&highlight=cli-companion").

---

### Post by TheFu on 2019-08-01
If you must use webmin (or any other webapp for system, ldap, DBMS management), please, only allow connections from localhost, so that an ssh tunnel is required to access the web interface.  This is also a good practice for management of blogs, especially if they are wordpress.  Harder to get hacked if the attacker has to gain access to the ssh first.

---

### Post by dragonfly41 on 2019-08-01
Another cranky idea, since I happen to be playing with VirtualBox and Vagrant on Ubuntu for other development goals.

> [COLOR=#000000]Is the a script anyone can help with, or maybe a package that checks mounted systems every say 5 minutes and if a mount is not present it reboots the system? [/COLOR]

Could you install VirtualBox on local Ubuntu server under your control and then leverage Synology Virtual Machine?

[https://www.synology.com/en-global/dsm/feature/virtual_machine_manager](https://www.synology.com/en-global/dsm/feature/virtual_machine_manager)

---

