---
title: "RDP style workflow holding me back"
date: 2017-03-23
forum: General Help
---

### Post by mrpoponz on 2017-03-23
Hi,

I'd love to switch to Linux/Ubuntu but there is one thing holding me back :(  This really pains me because I want to move off Windows really badly.

I've got an Android App and a Website that I've built as a hobby on the side.  It is a real labour of love.

I have a desktop machine running Windows 10.  I have Android Studio, Netbeans, GIMP, MySQL Workbench.  I decided to go open source with the tools to ensure that if I wanted to I could swap to another operating system.  The windows feature I've used since Windows XP Pro is the ability to RDP on to my desktop machine.  I can keep working where I left off, my session is redirected to a remote machine (laptop).  The geometry of the desktop will resize and all the applications will also resize as well.  It's really elegant as my laptop's resolution is pretty poor compared to the dual monitor setup I've got on my desktop machine.

But... I've been unable to find something almost identical.  I've looked at VNC with screen scraping, it didn't really perform well.  Any ideas?

Thanks,

- Paul

---

### Post by TheFu on 2017-03-24
Use NX protocol.  The most popular and easiest to setup is **x2go**. Before you touch that, setup **ssh** between the client and server first. Until ssh is working, x2go will not work. 

On all Unix systems, ssh is a way of life. Learn the main 50 things it can do to get the most out of it.

For x2go, you'll want to use THEIR PPA for the server-side install.  Also, follow their install/setup instructions - there is more to it than just install --> run, but it isn't hard.  On Windows clients, be certain to install the extra fonts.

BTW, I've been using x2go and other NX methods to access my primary Linux desktop from anywhere in the world from either a Windows or Linux client machine since 2011-ish.  My primary desktop doesn't actually have any GPU or monitor connected - it is only available this way or via direct ssh (which it how I use it most efficiently when traveling).

---

### Post by sp40140 on 2017-03-24
You can use TeamViewer. It has settings to match resolution. And also, it has decent mobile app as well. So if you want to go at it from a tablet, you can.

---

### Post by TheFu on 2017-03-24
The issue with trusting 3rd parties is that you have to trust their security. 
[TeamViewer confirms number of abused user accounts is ...]("https://arstechnica.com/security/2016/06/teamviewer-says-theres-no-evidence-of-2fa-bypass-in-mass-account-hack/")

For many people, this is fine.

ssh has had issues too, mainly on debian/ubuntu systems, so rolling your own isn't 100%.  Even if you'd done all the right stuff, there was a flaw in the ssh implementation because someone who saw code doing something that appeared to be worthless decided to remove it. That issue was cause, IMHO, due to poor code commenting of the block. The guy who originally coded it should have done better.  I say this as someone with 15+ yrs as a professional software developer.  The next guy shouldn't have to guess what a block of code does.

Anyway, there are lots of choices. There are probably faster VNC solutions than you attempted, plus there is SPICE for remote desktops at wire speed.  Don't think SPICE fits your needs, since it is for virtual machine. [https://www.spice-space.org/](https://www.spice-space.org/)  I've seen someone running autoCAD via SPICE inside a VM. It was impressive.

---

### Post by sp40140 on 2017-03-24
@TheFu.
True. TeamViewer has had problem. But it's the nature of the beast. No code is unbreakable. Having said that, TeamViewer is commercial grade software and I think it very likely that they have/ will take steps to make it better.
Anyways, not trying to get into argument. It was just suggestion based on OP's requirements. I have no personal / financial interest in TeamViewer.

Cheers,

---

### Post by howefield on 2017-03-25
> **sp40140 said:**
> Having said that, TeamViewer is commercial grade software and I think it very likely that they have/ will take steps to make it better.

Yes, I'm sure they will. However as the thrust of the article linked to is more about user and other third party security measures rather than their own, it'll be a tough nut to crack ;)

---

### Post by sp40140 on 2017-03-25
We can have never ending conversation about this. And it would be really off topic. 
Anyways this is OP's call to make as to which software to use.

Cheers & beers :)

---

### Post by sp40140 on 2017-04-02
Week old thread but I recently came across this thing which just might be what you are looking for:
[https://xpra.org](https://xpra.org)

---

