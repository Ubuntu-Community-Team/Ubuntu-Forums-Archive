---
title: "Held back packages - Phased updates"
date: 2022-12-13
forum: General Help
---

### Post by PantherStu on 2022-12-13
Hi all, 

after a long break from Linux and have come back to Ubuntu. 
I am just wondering if someone can tell me, just because im interested,  
So I have a few packages being held back when i try to update, and yes I know I can force them to update. I have looked at the information from apt-cache policy for each, and they are showing 0%, but have been showing like that for over a week.

I am just wondering
A. is there a website or somewhere I can look to find out why packages are being held back?
B. Why would a phased update stay at 0% for an extended time?

Just genuine enquires.
Thanks in advance for your answers.

---

### Post by Paddy Landau on 2022-12-13
Phased updates used to be hidden behind the Software Store, but apt would ignore that and just update the packages anyway.

apt has been updated to honour the phased updates, which is why you now see them. The reasons are good: To catch bugs when only a few people have updated.

The timing is shared around, so right now, you're a week into the wait, but another time, your wait will be shorter, and yet another time, you'll be first in line!

Urgent security updates aren't phased because of their importance.

You have several options:

[LIST=1]
[*]Continue to wait. This is recommended.
[*]Force the updates as follows. Do this only if you have a specific reason to force these specific updates.
```
sudo apt -o APT::Get::Always-Include-Phased-Updates=true upgrade
```
[*]Tell apt to ignore phased updates, and always put you first in line. Obviously, this isn't recommended, so do it at your own risk.
[LIST=1]
[*]Create the following file. Check that the permissions are the same as other files in that folder.
[FONT=courier new]/etc/apt/apt.conf.d/90disable-phased-updates[/FONT]
[*]Insert the following contents:
```
// Disable phased updates.
APT
{
    Get
    {
        Always-Include-Phased-Updates true;
    }
}
```
[/LIST]
[/LIST]
I don't know how to find the list of phased packages, sorry.

---

### Post by deadflowr on 2022-12-13
Pending updates: [https://people.canonical.com/~ubuntu-archive/pending-sru.html]("https://people.canonical.com/~ubuntu-archive/pending-sru.html")
Current updates being phased: [https://people.canonical.com/~ubuntu-archive/phased-updates.html]("https://people.canonical.com/~ubuntu-archive/phased-updates.html")
Note that Errors linked are only accessible to privileged developers, so you'd probably have to search bugs for the specific package you want to know more about on launchpad.

---

### Post by Paddy Landau on 2022-12-13
> **deadflowr said:**
> Pending updates: [https://people.canonical.com/~ubuntu-archive/pending-sru.html](https://people.canonical.com/~ubuntu-archive/pending-sru.html)
Current updates being phased: [https://people.canonical.com/~ubuntu-archive/phased-updates.html](https://people.canonical.com/~ubuntu-archive/phased-updates.html)
That is interesting. I note in the second link that 3 out of the 7 phased updates have been halted due to errors. Phased updates are clearly of great benefit.

---

### Post by ajgreeny on 2022-12-13
I have been using **apt update** and **apt full-upgrade** for a very long time and the phased updates have never presented any problems or difficulties.

My very strong recommendation is to not worry about this at all but just continue as if the phased updates had not even been notified to you; as mentioned there are good reasons not to rush updates particularly if you value stability.

---

### Post by ian-weisser on 2022-12-13
To determine if a held-back package is due to phasing, simply run "apt-cache policy <packagename>":

Example:

```

$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 43.0-1ubuntu2
  Candidate: 43.1-0ubuntu1
  Version table:
     43.1-0ubuntu1 500 **(phased 10%)**
        500 http://us.archive.ubuntu.com/ubuntu kinetic-updates/main amd64 Packages
 *** 43.0-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu kinetic/main amd64 Packages
        100 /var/lib/dpkg/status

```

The **(phased xx%)** string shows ONLY when phasing is occurring. It will be absent if the package is not phasing and thus eligible for immediate upgrade...assuming the package is not 'kept back' for some other classic reason, like a version conflict.

---

### Post by Paddy Landau on 2022-12-14
Question: How do I get a list of upgradable packages *excluding* those held back?

For example, right now, when I issue [FONT=courier new]apt list --upgradable[/FONT], it lists five packages. But when I issue [FONT=courier new]sudo apt upgrade[/FONT], it updates one package and lists the other four as held back.

I'd like to have a command that lists only the ones that will actually be upgraded.

Do you know how to do this?

---

### Post by PantherStu on 2022-12-16
Thankyou everyone for the replies.

As i said, phased updates didn't worry, was more just interested. 

And a special thankyou to deadflowr, this was exactly what i was looking for.
> **deadflowr said:**
> Pending updates: [https://people.canonical.com/~ubuntu-archive/pending-sru.html](https://people.canonical.com/~ubuntu-archive/pending-sru.html)
Current updates being phased: [https://people.canonical.com/~ubuntu-archive/phased-updates.html](https://people.canonical.com/~ubuntu-archive/phased-updates.html)


---

### Post by Paddy Landau on 2023-01-18
I have a question.

When I ask to see pending updates, I see all pending updates including ones that are held back. For example, today:
```
$ [B]apt list --upgradable
[/B]Listing... Done
alsa-ucm-conf/jammy-updates,jammy-updates 1.2.6.3-1ubuntu1.2 all [upgradable from: 1.2.6.3-1ubuntu1.1]
python-apt-common/jammy-updates,jammy-updates 2.4.0 all [upgradable from: 2.3.0ubuntu2.1]
python3-apt/jammy-updates 2.4.0 amd64 [upgradable from: 2.3.0ubuntu2.1]
update-notifier-common/jammy-updates,jammy-updates 3.192.54.3 all [upgradable from: 3.192.54]
update-notifier/jammy-updates 3.192.54.3 amd64 [upgradable from: 3.192.54]
```
This shows all pending updates. But when I try to update, in fact they are all held back:
```
$ **sudo apt upgrade**
        :        :        :
        :        :        :
The following packages have been kept back:
  alsa-ucm-conf python-apt-common python3-apt update-notifier update-notifier-common
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
```
How can I list only those that are not held back, i.e. only those that will actually be updated?

---

### Post by michael351 on 2023-01-24
I noticed today when I updated I saw:
> The following packages have been kept back:
  libnvidia-cfg1-525 libnvidia-compute-525 libnvidia-compute-525:i386
  libnvidia-decode-525 libnvidia-decode-525:i386 libnvidia-encode-525
  libnvidia-encode-525:i386 libnvidia-extra-525 libnvidia-fbc1-525
  libnvidia-fbc1-525:i386 libnvidia-gl-525 libnvidia-gl-525:i386
  linux-modules-nvidia-525-5.15.0-58-generic linux-modules-nvidia-525-generic-hwe-22.04
  linux-objects-nvidia-525-5.15.0-58-generic linux-signatures-nvidia-5.15.0-58-generic
  nvidia-compute-utils-525 nvidia-driver-525 nvidia-kernel-common-525
  nvidia-kernel-source-525 nvidia-utils-525 update-notifier update-notifier-common
  xserver-xorg-video-nvidia-525

but when I ran: $ apt-cache policy gnome-shell 
I get:
> gnome-shell:
  Installed: 42.5-0ubuntu1
  Candidate: 42.5-0ubuntu1
  Version table:
 *** 42.5-0ubuntu1 500
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     42.0-2ubuntu1 500
        500 [http://mirror.team-cymru.com/ubuntu](http://mirror.team-cymru.com/ubuntu) jammy/main amd64 Packages

I don't see any current phasing of updates (as per Ian's post)?

---

### Post by Impavidus on 2023-01-24
The updates are all related to nvidia drivers or update-notifier. Check one of those and it should tell you about phased updates. gnome-shell isn't in phased updates anymore.

So to explain the anatomy of the command:```
apt-cache policy update-notifier
```runs the **apt-cache** tool, which can tell you about packages. You give it the **policy** instruction, which tells apt-cache that you want to be informed about the available versions of a package and what version takes priority. Then you give it the name **update-notifier**, which is the name of the package you want details on.

---

