---
title: "does rsync work in the backgroud?"
date: 2021-03-19
forum: General Help
---

### Post by Heeter on 2021-03-19
Hi all,

I ssh into all my servers from my laptop. 3 of them are kvm images sitting on a kvm host server.

I have a 131gig folder sitting on one kvm image, that I would like to transfer this folder to another kvm image.

Would rsync be my best choice? If I do rsync, will it run in the background in case I lose ssh connection from my laptop to the servers?

Never used rsync for such a huge task. Thought I better ask first than corrupt 2 servers.

Regards

---

### Post by TheFu on 2021-03-20
I don't know if rsync is the best choice, but it is a reasonable choice and part of the question asked.
[LIST]
[*]If you want rsync to detach from the ssh session, then run it detached. That's something like **cp /bigfile /mnt/newdisk/ &**  <--- detached.
[*]Or use **tmux** or **screen**.
[*]Or schedule it to run via **cron** or **at**.  cron uses crontabs and at can run stuff "now" or at a specific time or at a time delay. After it is scheduled, you can logout or disconnect. If the system it on at the time specified, that job will run with the complete environment in the shell being used.  I find it handy to pre-schedule deletion of files I won't need in a month, but need for a few weeks until some external processing happens - like filling out govt forms or posting a file for a friend to grab off a webserver I run.
[LIST]
[*]echo "./run something" | at now + 20 days
[*]echo "./run something" | at 5 pm
[*]echo "rm /path/to/temp/file" | at 7 am Fri
[/LIST]
[*]Or use taskspooler to run it. It is in the repos. I love taskspooler for long running jobs. All the output gets put into a file, automatically, and if there are multiple jobs, they can be queued so that only 1 or 5 or 20 are allowed to run concurrently.  **tsp cp /bigfile /mnt/newdisk/**
[/LIST]

The great thing about rsync is that it can be run over and over and over again with the same command. If files have already been transferred, and haven't changed, then they will not be transferred again.  The bad thing about rsync is that you have to know the options to manage the sync of files, which you might want to have delete files that are not in the source tree any longer.  Also, sparse files need a special switch to safely transfer without exploding in size and .... well - learn to use the *--dry-run* option before doing large transfers, so you can check what would happen before you actually do the job.  Also learn about the use of the trailing / at the end of source directories. That will get files that would otherwise not be included.
```
rsync -avz /tmp /backup-target/
 vs
rsync -avz /tmp/ /backup-target/
```
It can matter.

If you plan to transfer a running OS, be aware that open files can result in corrupted transfers.  If I'm transferring files a running OS, then I'll run the rsync first just to get most of the files to the new storage. That new storage would be powered off or running a temporary OS from different media. Then for the final transfer, to ensure no corrupted files remain, I'd shutdown both sides, use alternate boot media (just connect a Try Ubuntu ISO), mount the source and target storage, then redo the rsync transfer. This should be very fast and only update perhaps 100 files that were modified since the first transfer happened.  The 1st transfer might take 1+ hours.  The 2nd transfer to true up any changes might take 30 seconds.

If you just want to clone a KVM image file, use **qemu-img**. It won't work for logical volumes provided as block devices to VMs, but it will handle vdi, qcow2, qcow, vmdk, vhd, vhdx, qed and raw images.  Be certain you aren't using a btrfs file system to hold any CoW VM storage.  CoW placed onto CoW seems to encourage corruption. It is a known problem. Btrfs has a way to disable CoW features, I think.

Have you considered creating another storage device just for this directory?  Then you'd only change the pointer in the VM definition XML file (virsh edit "VM Name") and not actually need to move the data.  Just thinking out loud with this idea.  Actually, I think this is the best choice now.

---

### Post by The Cog on 2021-03-20
^^^ What TheFu said.
My first choice would be to install screen and run rsync inside there. Screen gives you a console that will continue to run even if you disconnect. Then you can reconnect at any time and see how far it got. ssh to the machine you want to run rsync on:
```
# install screen: 
sudo apt install screen
screen
rsync blah blah blah
# Detach from screen
Ctrl+A d
# Log out ssh
exit
# Re-connect and re-attach 
ssh user@host
screen -r
```
If a network problem disconnects you while you are using screen, you just ssh back in then re-attach.

If both VMs are on he same host it may be an idea to make a new disk image, attach it to the sender, copy the files onto it, then attach it to the receiver instead and copy the files off.

Edit: It occurs to me that there is an unspoken assumption behind this conversation: If you lose connectivity and your SSH session disconnects while you are running something on the remote machine, then yes, normally what you are running would get killed off. This whole conversation is about how to avoid that interruption to the remote program.

---

### Post by HermanAB on 2021-03-20
Linux is UNIX.  Any program can be made to run in the background unattended, if you want it to.  There is always a way to do that.

The suggestion to use screen is a good one for this case.

---

### Post by Heeter on 2021-03-22
Awesome, Thank you guys for all your input,

Really appreciate it.

---

