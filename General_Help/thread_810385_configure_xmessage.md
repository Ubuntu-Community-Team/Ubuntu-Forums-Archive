---
title: "configure xmessage"
date: 2008-05-28
forum: General Help
---

### Post by maarten80 on 2008-05-28
I did a minimal install of ubuntu and am using openbox as a windowmanager. Works pretty slick on my old laptop.

To make it more accessible for 'non-geek' users I installed xdm and configured a login-screen. So far so good.

On this page I found some info on configuring the login-screen.
[http://gentoo-wiki.com/TIP_XDM_Login_Screen_Customization]("http://gentoo-wiki.com/TIP_XDM_Login_Screen_Customization")

One of the tings I want to add is a shutdown/reboot button as described on the page. They use xmessage to do that. I succeeded in getting the buttons but they look very ugly. How can I configure the appearance of xmessage?

I already found that editing Xresources helps, but can't seem to find the correct options for configuring xmessage. (such as xmessage*background)

For instance, I want to make the buttons rectangular and change the fonts.

As an aside: Is xmessage still frequently used or are there better alternatives? I'd like to stay away from gdm or kdm applications as they might tax my system more.

---

### Post by urukrama on 2008-05-28
Have a look at [this post]("http://urukrama.wordpress.com/2007/12/03/confirm-to-shut-down-reboot-or-log-out-in-openbox/"). I uses gmessage, which follows your gtk theme, and therefore looks nicer than xmessage.

---

### Post by maarten80 on 2008-05-28
Wow, thanks for the fast response! I read something about when first checking your site but didn't recall. I will definitely try it.

On a related question: How do you change the backgroundcolor of the Openbox menu itself? I'm confused about what setting that is in the themerc.

---

### Post by urukrama on 2008-05-28
That would be "menu.items.bg.color:" ("menu.items.bg:" controls the pattern: flat, solid, raised, gradient, etc.)

The [theme documentation]("http://icculus.org/openbox/index.php/Help:Themes") is quite good and explains it further.

---

### Post by maarten80 on 2008-05-28
Ah, I thought that would also change the color of other menus, but these are probably controlled by the gtk theme rather than the openbox theme, right?

Excuse me my ignorance, but I'm rather new to all this editing.

Thanks again!

---

### Post by urukrama on 2008-05-28
> **maarten80 said:**
> Ah, I thought that would also change the color of other menus, but these are probably controlled by the gtk theme rather than the openbox theme, right?

Yes. The Openbox theme only controls desktop menus, the client-menu (right click on a window decoartion), the window decoration, and the on-screen-display (alt-tab, change desktop).

All aspects of the Gtk applications are controlled by the Gtk theme.

---

### Post by the dsc on 2008-09-10
[sorry, wrong info, as I've checked)

---

