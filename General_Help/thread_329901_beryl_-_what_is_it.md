---
title: "beryl - what is it?"
date: 2007-01-02
forum: General Help
---

### Post by Cirrocco on 2007-01-02
I have some general questions about beryl - namely what is it?
I already know that it's a 3d desktop interface with nice effects and eye candy.

But is it a Desktop Environment parallel to Gnome?
   -if so, do you select it as a session like you would for Gnome or KDE?

Is it a window manager that runs inside of Gnome?
  -if so, is it specific to the desktop environment (IE: I installed in on Gnome, so when I run KDE I don't see it)

If I install Beryl along with some proprietary video drivers from Nvidia - and then I update my kernel (Thus breaking my video driver)
- will I be able to recover my Beryl installation after reinstalling the Nvidia drivers?  
-or will I have to reinstall Beryl, too?

yes, I read the [Beryl FAQ]("http://wiki.beryl-project.org/index.php/FAQ/Beryl")
> What is Beryl?

Beryl is a combined window manager and compositing manager that runs on top of Xgl or AIGLX using OpenGL to provide effects accelerated by a 3D graphics card on the desktop. 
but that doesn't address *my* questions

anyone out there know?

---

### Post by eggdeng on 2007-01-02
Here goes. Beryl is a  window-manager. On gnome, for example, it runs in place of metacity. With ATI cards you need to have the fglrx drivers installed, with nvidia, the latest proprietary drivers to provide 3d acceleration.
When you first install it, it's a good idea to configure it to be able to choose an XGL session in the session manager. That way, if it screws up, you can still log in to your user, but you can of course configure it as the default session.
I have no experience of Beryl on KDE, so I can't help you with this . The last question, I'm pretty sure the answer is yes, you will have to reinstall but it's worth the pain. Beryl is more than just eye-candy, it really helps you to take advantage of your workspaces besides giving a completely different feel to the desktop. I've had windows-junkies slavering over my laptop begging for a ubuntu cd. Just that would be sufficient reward.

---

### Post by Dies on 2007-01-02
In case of a kernel update you will need to re-install the video drivers but not beryl.

---

### Post by ayoli on 2007-01-02
> **Cirrocco said:**
> I have some general questions about beryl - namely what is it?
I already know that it's a 3d desktop interface with nice effects and eye candy.

But is it a Desktop Environment parallel to Gnome?
   -if so, do you select it as a session like you would for Gnome or KDE?

no it is not a desktop envirnment, but you can have it as a session choice (there are some howtos about this method)
> **Cirrocco said:**
> 
Is it a window manager that runs inside of Gnome?
  -if so, is it specific to the desktop environment (IE: I installed in on Gnome, so when I run KDE I don't see it)

no, it's not DE specific, you can use it with gnome, kde, xfce or whatever
> **Cirrocco said:**
> 
If I install Beryl along with some proprietary video drivers from Nvidia - and then I update my kernel (Thus breaking my video driver)
- will I be able to recover my Beryl installation after reinstalling the Nvidia drivers?  
-or will I have to reinstall Beryl, too?

no you will just have to reinstall proprietary drivers not beryl.

---

### Post by Azakus on 2007-01-02
I'd recommend going the AiGLX route instead of using Xgl. I had only problems with Xgl, and AIGLX is built into Egdy, so there really is no need to use Xgl.

---

### Post by Cirrocco on 2007-01-03
so if it's installed as XGL - it can be setup as a session

but if it's installed using AiGLX - there are less problems?

---

### Post by Waappu on 2007-01-03
Hi

I personaly see this just like that. I have try both way and find out that my skills or my PC HW isn't good for XGL setup =). AiGXL was painles and working great for me.

---

### Post by Azakus on 2007-01-03
Yes, with XGL you should set it up as a separate session (and it will use a different "monitor" too). XGL renders everything with screen 1, while AIGLX renders through the default of screen 0. The difference is that if XGL crashes, you can flip back to screen 0 and still be up and running, while if AIGLX crashes, you're stuck with a reboot (although I've never had AIGLX crash, which I can't say for XGL). However, Playing video through XGL is a CPU nightmare (~70% usage) because all the video is CPU rendered then. It can be easily displayed normally with a command before executing the program, but that doesn't happen under AIGLX. Personally, I use AIGLX because my video card supports it and I had a lot of problems with XGL.

---

