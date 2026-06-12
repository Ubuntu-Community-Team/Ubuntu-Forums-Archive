---
title: "Minimal Bash-like line Error"
date: 2020-02-10
forum: General Help
---

### Post by humptydumpti on 2020-02-10
Hi,

My computer says minimal bash line ediditing is supported error. 


grub>_


After a bit of research i found out its a common error. I tried to fix it via 

**2nd option : install Boot-Repair in Ubuntu**

 - either from an Ubuntu live-session ([boot your computer on a Ubuntu live-CD or live-USB]("https://help.ubuntu.com/community/BootFromCD") then choose "Try Ubuntu") or from your installed Ubuntu session (if you can access it) 
- connect to the Internet 
- open a new [Terminal]("https://help.ubuntu.com/community/Terminal"), then type the following commands (press Enter after each line): 
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

That did not work. It cried i use files that are not yet programmed. I then wanted to copy my files from the old ubuntu and install a fresh ubuntu. To my suprise i only have access to the windows files. 

Now my question is, how can i secure the files from old ubuntu?

many thanks in advance

---

### Post by yancek on 2020-02-10
What didn't work?  The commands you posted are to download and install boot repair.  Did you run boot repair selecting the option to Create BootInfo Summary?  Without that and the minimal info you posted, I don't think there is much anyone can do to help.  Run boot repair with that option and post the link you get when it completes.  Do NOT try any repairs.

---

### Post by Impavidus on 2020-02-10
Which version of Ubuntu is installed? Which version of Ubuntu is on your live disk? Can you show us the exact and complete output of every command you run (and show the commands too)? You can simply copy text from the terminal and paste it in your web browser.

---

### Post by TheFu on 2020-02-10
> **humptydumpti said:**
> 
My computer says minimal bash line ediditing is supported error. 
That is purely a convenience reminder. It is not an error message.  grub's command prompt supports minimal cmd line editing. If you don't know what that means, don't worry about it. If you are good on the bash command line, entering and modifying text are much easier.
   
> **humptydumpti said:**
> Now my question is, how can i secure the files from old ubuntu?
 

"secure"?  Do you mean copy? Or do you want to encrypt them so nobody else has access?  "secure" has different meanings which need more context to convey.

If you want to copy the files off, use a USB flash "Try Ubuntu" boot environment and copy the flies off to some other storage. It can be on the network, another SATA disk or another USB storage device.

Boot-repair hasn't been good at repairing boots in about 5 yrs.  It is good at gathering data and providing a URL you can post here for more help.

---

