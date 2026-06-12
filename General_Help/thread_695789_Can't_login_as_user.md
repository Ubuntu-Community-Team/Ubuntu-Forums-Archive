---
title: "Can't login as user"
date: 2008-02-13
forum: General Help
---

### Post by Kreuger on 2008-02-13
I don't know what I did but I can't login anymore. When the XDM login screen comes up I put in my username and password and it starts loading then it seems to glitch and goes back to the login screen. The only change I've made lately was removing evms because I didn't think it was needed. This seemed to mess up my hard drive because when I rebooted it kept giving me I/O buffer errors and wanted to force a check so it did that and said I'd have to do it manually so I did that and went through about an hour of letting it fix whatever errors it had and now I have this problem. I can login as root using recovery mode and that lets me in fine. I went into pcmanfm and went to my home folder to see about backing everything up that I want so I could reinstall and it told me that my home folder doesnt exist but I still do as a user. I'm wondering if it maybe erased my home directory because a lot of the problems it seemed to want to fix were in there. But they were actually in the configuration folders for all my programs such as /home/kreuger/.firefox.  So now I'm not sure what to do. At the login screen I tried to load a virtual terminal to login but when I hit CTRL ALT and F1 it just goes blank and no terminal comes up, I cant even type. I tried using older kernel versions because it updated a couple of days ago but it didnt make a difference.

---

### Post by Kreuger on 2008-02-13
Anyone have any ideas?

---

### Post by SpaceTeddy on 2008-02-14
sounds as if gnome fails somewhere. why i cannot tell (need more information)... yet where do dig i don't know myself. try in any file in /var/log to see if anything throws errors.
A bling guess could also be that your configuration is broken. in that case, try with a blank homedir and see how the login reacts to that (or simply try login in as a different user)

as for the blank terminals, i've had that problem before. Disable the splash in grub (do that by editing the boot line in grub to remove the splash at the end) and the terminals should reappear (as long as gdm running and is not restarting all the time)

---

### Post by Kreuger on 2008-02-14
I'm using Fluxbox if that makes any difference. I'll look through the logs and see what I can find and try disabling the splash to see if that makes a difference.

Edit: Couldn't find anything in the logs that pointed to what was going on. I tried to install evms again through Synaptic but it wont download the files from the server even though Im online

---

