---
title: "GUI Notification of RAID Failure?"
date: 2008-02-24
forum: General Help
---

### Post by rocktorrentz on 2008-02-24
I am setting up my old PC to give to a friend who wants his own computer and is very interested in trying out linux. I have two 40GB hard disks which I can use but both of them are fairly old and although they have shown no sign of being unreliable, probably won't last that long. I am fairly experienced with linux software raid (I run a debian file server with RAID-5 which has been brilliant) and so am quite happy to set the pc up with a RAID 1 array for the both the root and home partitions for complete (well nearly) data security. However if one of the drives does fail or start producing errors, how will my friend know there is a problem (besides a system slowdown)? Is there some kind of program which runs in the notification area which will notify him of a problem or will the system just refuse to boot when the array is degraded?

Thanks in advance

---

### Post by fjgaude on 2008-02-24
I think something like this works if a failure or disk errors start showing:

```
sudo mdadm --monitor --mail=youremailaddress --delay=30 --scan
```

I've not done it but others have. Not sure how the email gets out of the system or what mail program to use. Some use Sendmail.

Let us know what you end up doing.

---

### Post by rocktorrentz on 2008-02-24
I might set up sendmail to use the gmail smtp server and the my email account to send me an email if anything goes wrong. I'll set up ssh anyway so I can help him out if he has any problems.

---

### Post by fjgaude on 2008-02-24
Let us know what you do and if it is successful... many here would gain understanding from your work.

Our software raid would be more universal if we had a GUI to control, setup, mdadm's features. I think that Novell's version has one, but it is rpm-based, and I'm not even sure if it uses mdadm as its base.

I've been using mdadm for about a year now and it is solid, without bugs. It has been difficult to learn the features and how to use them. But I'm sold on it as long as I only use six or less drives in raid5 with my SATA controller bus limitations, PCI-e X1, 500MHz throughput.

Good luck with what you are doing.

---

