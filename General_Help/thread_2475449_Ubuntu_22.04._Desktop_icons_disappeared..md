---
title: "Ubuntu 22.04. Desktop icons disappeared."
date: 2022-05-27
forum: General Help
---

### Post by m-elodie on 2022-05-27
Hello!

I already posted this question a few hours ago but I don't see it listed...
I have made a fresh install of Ubuntu 22.04 and it's working fine. There was no problem for
about a week, but since today, all my desktop icons have disappeared.
The .desktop files still exist in the Desktop folder, but they are not shown anymore.

Did anybody experience this? Does anybody have a solution for me?

Thanks for any hint.

Elodie.

---

### Post by Dennis N on 2022-05-27
Check that the Gnome shell extension "Desktop Extensions NG (DING)" is turned ON. Otherwise, no icons will appear.

---

### Post by jonfisher on 2022-05-27
> **Dennis N said:**
> Check that the Gnome shell extension "Desktop Extensions NG (DING)" is turned ON. Otherwise, no icons will appear.

Thanks for the link to that post.

I can drag a file from other folders to the desktop and they will appear on the desktop.  I just saved a file from Gimp to the desktop and it appears on desktop.    It seems that files saved from a web browser page are the ones that won't.

(?)   Have you attempted to save a file from a browser page?

Update:  I just attempted to save files from a browser page to the desktop with my laptop, and the files DO appear on the desktop when using it.  I wonder what the difference between my desktop and laptop could be, as I did a fresh install of Ubuntu 22.04 lts on each machine not long ago.   Hmmm.....

---

### Post by Dennis N on 2022-05-27
@jonfisher

You should be posting in your own thread. I will put a response there.

---

### Post by m-elodie on 2022-05-27
Hello!

Thanks for your reply... but where do you find this setup panel? I checked in settings, but there is nothing
like that.
And beside this, why did it change? It's been working just fine for about a week.

Thanks for any hint!

Elodie

---

### Post by Dennis N on 2022-05-28
> **m-elodie said:**
> Hello!
Thanks for your reply... but where do you find this setup panel? I checked in settings, but there is nothing
like that. And beside this, why did it change? 
Elodie
Are you referring to post #2? If so, the screenshot is of "Extensions Manager", and you can install it from Ubuntu Software. See the screenshot attached to this post showing two search results. You would install the first one (with the arrow). I'm not sure the extension is your problem, but it's worth checking. Besides that Extensions Manager is an important utility to have - it finds and installs gnome-shell extensions without needing the web browser at all. It also notifies you of updates when they are available and will update your extensions.

---

### Post by m-elodie on 2022-05-30
Hello!

Thanks for your reply!
I have installed the extension manager, but the window is pretty empty. I have 2 items only in System Extensions,
one is Ubunti ApplIndicators, the other one is Ubuntu Dock. No trace of Desktop Icons NG.
Am I supposed to install this? But in this case, why did it work before (when I installed Ubuntu 22.04) without this DING extension?
Is there a way to fix it without installing further software? I guess that's only a matter of configuration that for some reason got
screwed up.

Thanks for any hint!

Elodie

---

### Post by Dennis N on 2022-05-30
> **m-elodie said:**
> Hello!

Thanks for your reply!
I have installed the extension manager, but the window is pretty empty. I have 2 items only in System Extensions,
one is Ubunti ApplIndicators, the other one is Ubuntu Dock. No trace of Desktop Icons NG.
Am I supposed to install this? But in this case, why did it work before (when I installed Ubuntu 22.04) without this DING extension?
Is there a way to fix it without installing further software? I guess that's only a matter of configuration that for some reason got
screwed up.

Thanks for any hint!

Elodie
I believe you need the gnome-shell extension "Desktop Icons NG" for any Desktop icons in Ubuntu 22.04. If you did a new install of Ubuntu 22.04, it should have been installed by default as a "System Extension". I can't explain why it isn't there now. But, you can fix this. The system extensions are from the Ubuntu repository. Use the terminal to install it:
```
sudo apt install gnome-shell-extension-desktop-icons-ng
```
Afterwards, check Extensions Manager to be sure it is ON.

---

### Post by m-elodie on 2022-05-31
Hello Dennis!

Thanks for your reply. I installed and since there was still nothing in the extension manager, I rebooted.
And even without touching the extension manager, my icons are back. So I'm not sure what went wrong,
but for sure I didn't have to switch the icons on in extension manager.

Thanks!

Elodie

---

### Post by imgst on 2023-04-05
Where to find this? in settings? or?

---

### Post by mIk3_08 on 2023-04-06
> **m-elodie said:**
> Hello Dennis!
Thanks for your reply. I installed and since there was still nothing in the extension manager, I rebooted.
And even without touching the extension manager, my icons are back. 
Elodie
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

