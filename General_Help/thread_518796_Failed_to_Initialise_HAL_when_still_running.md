---
title: "Failed to Initialise HAL when still running"
date: 2007-08-06
forum: General Help
---

### Post by digital006 on 2007-08-06
When I boot up I'm getting the failed to initialise HAL message.

When I check to see if it is running it find that it is without any errors. I've disabled it then re-enabled it but it didn't fix it.

Also I get the same message when trying to run ntfs3g-config (sp?), it then brings up the config box but won't allow me to check internal drives.

Can anyone help? I'd really like to be able to mount my second hard drive.

Cheers
Mike

---

### Post by Raymond Clark on 2007-08-06
My Ubuntu just started to do this after installing some themes, however when i restarted, the HAL failed to initialize message appeared. I fixed it by going into the synaptic package manager and reinstalling the following packages:

hal
hal-device-manager
hal-info

this seemed to work for me so its worth a try.

Also after i had done this all my drives appeared and DVD drive appeared to spin up and then the icon appeared on the desktop.

---

### Post by digital006 on 2007-08-07
Hi, thanks for replying. I reinstalled then restarted and still got the error. I did it again and still got the error.

Any more help would be greatly appreciated.

---

### Post by ashishgoel on 2007-08-07
i'm also havin the same prob and i update and restart....

---

### Post by ashishgoel on 2007-08-08
SOLVED

Re: the infamous Failed to initialize hal error

--------------------------------------------------------------------------------

I also suffered from this problem. After much searching, it seems that these hal issues might be the result of a recent hal update via Ubuntus automatic update system (just speculating).

Now, with me being a newbie at Ubuntu, take everything I say with a grain of salt. But, these are the steps I followed (gathered from a few other posts) that got me up and running again.

In short, you need to roll back the hal update. Below are the steps I followed to accomplish this.

First, when this error occured I lost all USB, DVD drives and also my network connectivety (wireless and wired).

The line below allowed me to restart dbus and hal (I needed to get my connectivity back for the roll back).

sudo /etc/init.d/dbus restart

Whatever the above line did, it allowed me to manually reconfigure my wired connection (even though it didn't look like it was working, I was able to connect to the internet).

I then followed the instrucitions below to force the hal rollback.

The info below was pasted from a thread titled "Recent HAL update caused frequently failure for "suspend when lid closes"

************************************************** *********************************

Re: Recent HAL update caused frequently failure for "suspend when lid closes"

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...

---

### Post by jimmysl on 2007-08-11
Hi, I'm having the same problem it seems with HAL failing to initialize. It happened for me after I updated as well. I'm a newbie so I don't really know much about Ubuntu but I've done alright so far.

The problem for me is that I need to force ubuntu to use the previous version of HAL like it says in the previous post, but because HAL is down I can't access the internet and I'm not sure how to do it.

The previous post mentioned using > sudo /etc/init.d/dbus restart, I ran that but I don't know how to manually configure my Internet. 

I have Motorola sbg900 gateway, so I should be able to connect via Ethernet, usb, or wireless, but I haven't had any luck with any of them.

If someone could walk me through getting the Internet working I know how do the downgrade to the previous hal packages.

Any help would be appreciated, I don't really feel like doing a clean install again....

Cheers,
James

---

