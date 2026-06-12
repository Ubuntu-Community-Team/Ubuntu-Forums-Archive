---
title: "Is it possible to have an X-Session over ethernet to a laptop?"
date: 2013-04-21
forum: General Help
---

### Post by xZachtmx on 2013-04-21
I hope this is the right section to post in, and please forgive me if  what I am asking is crazy.  I have always heard that linux has always  been able to have multiple sessions for multiple users running simultaneously.  I have learned how to start a new x-session with startx -- :1, and I am able to switch to it with CTRL+ALT+F8.  

First of all everything works fine but the unity panel doesnt show up in the second session, is there a way I can open it?  

My second question is instead of somehow connecting to this x-session with a separate mouse, keyboard, and monitor, would there be a way for me to use a laptop with an ethernet cable connected?  So the laptop has all the needed input and output hardware, I just dont know how to  connect it to the second x-session (again not sure if this is possible).  Would the laptop  be able to notice a delay when using a word processor when connected over ethernet?  

That is all I have been wondering, It would be really neat if something like this could work.  I think you for taking the time to read this, and any suggestions or tips are greatly appreciated!

---

### Post by CatKiller on 2013-04-22
The concept you're talking about is called a thin-client and has been around forever. Personally I find it simpler to run individual programs over the network using X-forwarding than having a whole session per user. Also, a full desktop over the network is rather bandwidth-intensive, which is why compression schemes like RDP exist.

None of this means that if you have an itch to scratch and want to have a play that you shouldn't, it just means I don't know how to do it :)

---

### Post by steeldriver on 2013-04-22
I don't think startx provides all the stuff that is needed to run a unity session - that's likely why the panel doesn't display. You may have better luck with a different session.

Instead of starting the alternative session in a local tty you can look at something like vnc4server to instantiate it - you can request a specific display on the command line or let vnc4server choose the next free number. Then connect over the network using any VNC client. You should use ssh tunnelling if you are doing this over a public network.

[http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/](http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/)

---

### Post by tgalati4 on 2013-04-22
*Synergy* allows you to send keyboard and mouse commands over the network:

tgalati4@Mint14-Extensa ~ $ apt-cache search synergy
quicksynergy - GUI for easy configuration of Synergy
synergy - Share mouse, keyboard and clipboard over the network

I don't run Unity, but with gnome you can run gnome-panel (or mate-panel if you are running Mate) and you will get a complete remote desktop on one workspace.

You would do something like:

Remote login:  ssh -2 -Y username@remotecomputername
Start the desktop:  gnome-panel

Stand back in amazement.  I think the current xserver can handle up to 10 displays.

---

