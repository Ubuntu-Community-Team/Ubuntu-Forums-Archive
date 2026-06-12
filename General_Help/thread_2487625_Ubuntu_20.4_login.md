---
title: "Ubuntu 20.4 login"
date: 2023-06-10
forum: General Help
---

### Post by imaging2022 on 2023-06-10
Hello,
I can't login to Ubuntu 20.4 for unknown reasons. When it prompts for the password, I enter the password, and it looks like it is going to login, but unfortunately, it returns me to the login page again. Any hints, please? I don't want to lose the data.
Thanks in advance,

---

### Post by Bashing-om on 2023-06-10
imaging2022; Hello - Welcome to the Forums :D

A login loop can be caused by a large number of things - >> Let's see what we can find out :D

- rarely is it needed to take that nuclear option and re-install - ubuntu is always always fixable >> though sometimes the gain is not worth the effort. 

> 
 I don't want to lose the data.

We also see what we can do that such does not happen :D

OK - so what can you boot to ?
How about trying to boot to grub's boot menu and here select "advanced options" >> recovery kernel.
In the resulting menu select " failsafeX  " .
What Happens ?

We need to activate a terminal, somehow, to do some digging - this is but one way.
Once we have a terminal we can begin the diagnostic processes to find a cause.

[INDENT]small steps 
still get us a valid end
[/INDENT]

---

### Post by TheFu on 2023-06-10
> **imaging2022 said:**
> [COLOR=#232629][FONT=-apple-system]Hello,[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I can't login to Ubuntu 20.4 for unknown reasons. When it prompts for the password, I enter the password, and it looks like it is going to login, but unfortunately, it returns me to the login page again. Any hints, please? I don't want to lose the data.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Thanks in advance,[/FONT][/COLOR]

a) please use the standard fonts when posting here.  Your post seems to want the apple-system font, which nearly nobody here will have.

b) Nobody can answer based on the information provided. There are 1000s of reasons that could happen.  What did you do since the last reboot that could have caused this issue?  If you don't know or have forgotten, then you'll need to boot from an Ubuntu Install ISO (like you used to install Ubuntu), choose the "Try Ubuntu" option and start looking at the logs on the internal storage, not the USB flash drive you booted from.  Those looks should have warnings or errors that clearly say what the problem is.

BTW, it is "20.04".  The month part is 2 digits in Ubuntu releases.  If you are running a non-Ubuntu distro, that could be important, even if it is based on Ubuntu.

---

### Post by imaging2022 on 2023-06-12
Thanks.
I tried advanced options>> recovery kernel and I managed to see some options among of them was the failsfeX. Unfortunately everything gets frozen at this stage.

---

### Post by Bashing-om on 2023-06-13
imaging2022; Well -- Not

Let's see if we can gain a terminal another way.
 To boot to terminal from grub:
At the grub menu press 'e' to edit -
Append: systemd.unit=multi-user.target to the linux line.
ctl+x to continue booting.

Now what have we to work from ?

[INDENT]where there's a will there's a way
[/INDENT]

---

### Post by TheFu on 2023-06-14
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) could be helpful.  It uses a flash drive setup like an installer, but then we go into "Try Ubuntu" mode and setup a **chroot** environment to run the installed software on the internal disk. This skips the boot issue from the installed boot files.  We can fix those next.

See the **Update Failure** section for how to create a chroot. There are 2 other sections following that one which could be helpful if you don't know them already.  You'll need to manually **mount** the internal storage file systems to make this all work. That is often too complex for people unfamiliar with Linux device names.
I've had a system installed drive fail and ran for a week without it using this "live boot" method as I waited for the replacement hardware to arrive.

Everything done will only be retained if written to the internal storage device. If you install software BEFORE setting up the chroot, it won't be retained.

In theory, recovery mode will let you get into another minimal environment, but it doesn't always work, as you are seeing.


Bashing-om is better at this than I am, so maybe he can clarify the chroot method better?  IDK.  Maybe we aren't there yet.  I tend to jump to that ASAP because it always works, even if it is more complex than other methods.

---

