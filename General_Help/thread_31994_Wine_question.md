---
title: "Wine question"
date: 2005-05-05
forum: General Help
---

### Post by maruchan on 2005-05-05
I need some help with Wine. Any help is appreciated.

Description: 

I installed the Wine package. Also installed WineSetuptk because it says it's a configuration/setup tool. I had placed the WineHQ repositories in my sources area.

I ran "winesetuptk" and it said I needed to "use wt2 on a command line".
So then I ran "wt2". Clicked on various startup messages: ok, yeah, ok, ok
Then it started me through all the options:
-Create fake windows drive...check
-Simulate windows reboot....exit, failure status 1
read the log, says "cannot find 'wineboot'"

? Anyone know why this would happen or how I can just start all over the right way? I feel like I've strayed from the path.

Thanks.

EDIT: I'm thinking there is some sort of problem with Apt Ignoring the repositories...see below.

---

### Post by shakin on 2005-05-05
Search in the tips and tricks forum for my how-to on installing DVD Decrypter (a search for 'Decrypter' will find it). It goes through installing and configuring Wine using Wine's own debian repository and winetools.

---

### Post by maruchan on 2005-05-05
Thanks for the reply. I went over to your thread. Here are the problems I'm having after following your instructions:

I added the lines to sources.list, then ran apt-get update, but apt-get update is showing an "Ign" before the Wine repositories as it updates. Is that a problem?

Also, it looks like I already had winetools, but when I start it (winetools) it tells me:
1. > Wine has not been configured for this user yet. Start Winetools with wt2 on a command line and go to base setup first. Go to all submenu entries before you install other software.

Then, it says:

2. > WineTools is tested with Wine versions 20040914, 20041019, 20041201, 20050111. You use a different version so the results are unpredictable.

Then I let it run through the process as described above. It still exits when it cannot find 'wineboot', like I said in the original post.

Any ideas?

---

