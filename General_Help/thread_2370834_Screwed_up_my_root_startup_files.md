---
title: "Screwed up my root startup files"
date: 2017-09-07
forum: General Help
---

### Post by madhartigan on 2017-09-07
Hey there!

Hoping this is a simple fix . . .

I was trying to get terminal colors for bash in my root account.

I copied the bash backup files from /etc/skel  (.bashrc and .profile) into the home folder for root.

```
cp /etc/skel/.profile ~/.profile
cp /etc/skel/.bashrc ~/.bashrc 
```

I ran those from my root account when I was able to access it.

Then I logged out of root so I could log back in and test the changes.

Now when I try to 'su' from my account, I get bounced right back to the same prompt

```

darryl@helios:/$ su
Password:
darryl@helios:/$ cd /root
-bash: cd: /root: Permission denied
darryl@helios:/$ sudo su
darryl@helios:/$ cd /root
-bash: cd: /root: Permission denied
darryl@helios:/$

```

Any ideas how I can get my root access back?  Thanks!!

---

### Post by madhartigan on 2017-09-08
Bump

---

### Post by Tadaen_Sylvermane on 2017-09-08
try this

```
sudo -i
```

followed by the darryl password. 

su isn't enabled on ubuntu by default. various reasons on that and they don't let it be discussed here. sudo is what you should be using.

---

### Post by coffeecat on 2017-09-08
> **Tadaen_Sylvermane said:**
> 
su isn't enabled on ubuntu by default. various reasons on that and they don't let it be discussed here.

Not so. The forum policy is more nuanced than that. See here: [https://ubuntuforums.org/showthread.php?t=1486138](https://ubuntuforums.org/showthread.php?t=1486138)

In a nutshell:

1. Logging into a root GUI is off-limits as far as the forum is concerned, but only the forum. Users are welcome to break their own systems in any way they choose, and keep the pieces, so long as they don't lead newbies up the same garden path here on the forum.

2. Enabling the root account is not off-limits in forum discussions, but we prefer that the pros and cons (mostly cons) of enabling the root account are explained, if the subject comes up.

---

### Post by madhartigan on 2017-09-08
Thank you for the replies and offering a suggestion. I appreciate any help that can be offered.

Here's the result of executing that command: 

```
darryl@helios:~$ sudo -i
[sudo] password for darryl: 
Segmentation fault (core dumped)
darryl@helios:~$
```

Any other ideas?

---

### Post by bilkay on 2017-09-08
If all else fails, boot from something like a livecd, mount your harddrive and undo (as root) the changes that screwed things up.

---

### Post by madhartigan on 2017-09-08
Pretty sure that's the path I'll have to take.  Just wanted to run it by the forum before taking that route.  Thank you!!

---

### Post by madhartigan on 2017-09-08
Anyone looking to solve this *specific* issue (no promises for anything other than this very specific issue), here's what I did.  Kind of dumb I didn't think of this in the first place . . .

```
sudo rm /root/.profile
sudo rm /root/.bashrc
```

Once this was performed, I had no problems accessing root through the use of the 'su' command.

All caveats and warnings regarding the use of su and the root account still apply.

---

### Post by bilkay on 2017-09-09
As much can be learned from other people's mistakes as their successes.

One comment: If you could `sudo rm` the files, you should also be able to `sudo {edit}` them.

---

