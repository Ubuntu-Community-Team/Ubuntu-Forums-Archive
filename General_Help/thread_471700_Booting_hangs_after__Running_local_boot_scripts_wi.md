---
title: "Booting hangs after  Running local boot scripts/ with a twist"
date: 2007-06-12
forum: General Help
---

### Post by platoniciedeal on 2007-06-12
I know others have posted this but I have yet to see an answer. I am running Kubuntu 7.04. Everything worked fine, until just one more tweak :-) I installed Bootup Manager (BUM) ran it, but did not shut down any starting process. I was just looking. I did uninstall brltty and ppp through Adept. Upon reboot the screen hangs at Running local boot scripts (/etc/rc.local). Black screen. ENTER does nothing. I can type words but login and password do not do anything. If I alt-F1 I can get CL, login and StartX This gets me into my GUI but certain user modified screen candy like loading screen, background, fonts and icons are changed to default. Oddlyy the cursors are still the modified ones. The rest of my profile is correct though, i.e., Thunderbird, Firefox bookmarks, all installed programs are correct. BUT if I get command line, login and type envy -t then hit option 7, Restart X, I get the GUI login screen instead of going directly to my profile. Some how the restart X option goes to a different place than StartX, giving me all of my screen candy goodness. 

On shut down from StartX solution it goes back to cli. On shutdown from envy -t it goes back to GUI login screen, then shutdown or restart from there goes to cli.

I have seen suggested solutions to double check the tty1-tty6 and make sure they are written correctly with the exec on the correct line. All of them checked out. NVIDIA Driver works fine still, is latest version. xorg.conf still gives me my dual monitors. Network, samba, everything is ok.

Although a relative newbie (using it for about a year), I am comfortable enough to explore all the startup scripts if someone can point me in the right direction.

Thanks,

---

