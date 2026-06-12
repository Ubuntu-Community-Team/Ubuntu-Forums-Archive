---
title: "Use Server edition or Mini.iso? to install a Desktop"
date: 2014-05-06
forum: General Help
---

### Post by ubume2 on 2014-05-06
****I have installed the server edition (14.04 64 bit) and mini.iso in my Virtualbox. On the server edition I choose manual install and install xorg, some essential apps and lxde.

I haven t noticed any difference between server manual install and mini.iso install other than installing from mini.iso takes **forever**, and the server installation cd is much faster.  

My purpose of using either of these is to avoid the fat of unity, plus the fun of installing from the ground up.

I have read here [HTML]http://askubuntu.com/questions/44185/[/HTML] that the server edition optimizes the kernel for server and implies that the desktop is slowed down.

Since I have not installed a specific server ssh or whatever is the kernel really optimized for server and slows down desktop? Are there any other disadvantages of using the server install cd when my purpose is to have a customized desktop?

Thank you.

---

### Post by oldfred on 2014-05-06
I do not use server version, but in release notes a couple of years ago I saw where they said they made the kernel the same in all versions. I just checked release notes for 12.04 so it may have been before that?

---

### Post by ibjsb4 on 2014-05-06
I have used both in the past and found them to be the same.  I have heard some say that the server edition will install extra server packages, but when doing just the command line install I have not seen this.

---

### Post by deadflowr on 2014-05-06
> I haven t noticed any difference between server manual install and mini.iso install other than installing from mini.iso takes **forever**, and the server installation cd is much faster.  

The server contains the files to install the core system, (ie the kernel, boot files, etc,etc)
The mini needs to download them off the servers then installs them.

I believe both need to download the selected packages, like LAMP, or Lubuntu-Desktop.

So server installs, initially, at a brisker pace, since it's installing directly from a disk or usb stick.
The mini install speed is rather dependent on the network speed you have.

---

### Post by ubume2 on 2014-05-06
@ oldfred that post i was referring to is dated May 21, 2011. 12.04 not available then.  The article also says The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition. Preemption is turned off in the Server Edition.The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition.  I have no idea what that means.  The article may be dated because it also says it is optimized for 686.

@ ibbjsb4 I haven't seen any difference either.
@ deadflower I am not into servers, but seems like the initial install is faster for the server edition. Since there apparently isn't an alternate install cd for 14.04, I am using server edition as my "alternate" install.

---

### Post by oldfred on 2014-05-06
Some discussion on schedulers.
[http://www.wilderssecurity.com/threads/ubuntu-now-uses-the-deadline-io-scheduler.343415/](http://www.wilderssecurity.com/threads/ubuntu-now-uses-the-deadline-io-scheduler.343415/)

       Ubuntu server uses CFQ scheduler instead of deadline
    [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1008400](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1008400)
Post #14 2012-07-25
>  We've changed default IO scheduler from CFQ to deadline for both server and desktop kernel. Please find our latest kernel from git tree for Quantal release, any test and bug report are welcome.



---

### Post by deadflowr on 2014-05-06
> **ubume2 said:**
> .
@ deadflower I am not into servers, but seems like the initial install is faster for the server edition. Since there apparently isn't an alternate install cd for 14.04, I am using server edition as my "alternate" install.

That's neither here nor there for me.
I was just posting as to the why it seems/is faster.

Server simply has the base system on the disk, mini does not.
All mini has the components to download the base system.

---

### Post by ubume2 on 2014-05-07
Thanks to all who replied. For my purposes I think the server edition cd will work fine for me,even though I have no intentions of creating a server.

IMO the server edition is faster (maybe initially). The mini.iso besides being initially slower, for me is possibly too basic. Maybe as I gain experience I will attempt it again. Thanks :)

---

