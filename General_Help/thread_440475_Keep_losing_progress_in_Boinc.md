---
title: "Keep losing progress in Boinc"
date: 2007-05-11
forum: General Help
---

### Post by eapache on 2007-05-11
I've had Ubuntu since Dapper, and I'm now running Fiesty. I recently installed Boinc, and despite the boinc website's assurances that it will pick up where it left off when you restart your computer, this isn't happening. Every time I restart my computer, I lose any work in progress. The task remains, and it doesn't have to redownload it, but the progress is reset to 0% and the CPU Time to 0:00.

It doesn't give any error messages. Does anybody know what's wrong?

BTW this is the first time I've used Boinc.

---

### Post by TransitMan on 2007-05-12
This is a common problem I've found when upgrading from version of Ubuntu to the next.
I just live with it and let it run.

Also, with the newest OS, the BOINC program recognizes a new OS, not the older on and therefore will reset. No work-around that I know of.

---

### Post by eapache on 2007-05-12
I installed Boinc after do a clean install of feisty, and every time I restart my PC, it resets. It's like it's failing to checkpoint or something. It doesn't have anything to do with running updates (i don't think).

---

### Post by TransitMan on 2007-05-12
When you shut down the PC, do you "Exit" BOINC first, or just shut down?

An option is to completely delete the BOINC folder and do a fresh install. It may have been possible that the initial install corrupted itself, as this has been known to happen.

---

### Post by Talon2 on 2007-05-12
> **eapache said:**
> I've had Ubuntu since Dapper, and I'm now running Fiesty. I recently installed Boinc, and despite the boinc website's assurances that it will pick up where it left off when you restart your computer, this isn't happening. Every time I restart my computer, I lose any work in progress. The task remains, and it doesn't have to redownload it, but the progress is reset to 0% and the CPU Time to 0:00.

It doesn't give any error messages. Does anybody know what's wrong?

BTW this is the first time I've used Boinc.

The old v5.4 that is in the repository isn't very good.  An updated v5.8.17 is available but can be quite a challenge to install.  Here are the packages I had to download and install from Debian unstable:

boinc-app-seti_5.13+cvs20060510-1ubuntu1_i386.deb
boinc-client_5.8.17-1_i386.deb
boinc-manager_5.8.17-1_i386.deb
gcc-4.2-base_4.2-20070502-0ubuntu2_i386.deb
libgcc1_4.2-20070502-0ubuntu2_i386.deb
libstdc++6_4.2-20070502-0ubuntu2_i386.deb

It appears that this new version will be in the repositories for Gutsy.  No idea if it will be backported for Fiesty.  This new version works very well here.

---

### Post by TransitMan on 2007-05-12
> **Talon2 said:**
> The old v5.4 that is in the repository isn't very good.  An updated v5.8.17 is available but can be quite a challenge to install.  Here are the packages I had to download and install from Debian unstable:

boinc-app-seti_5.13+cvs20060510-1ubuntu1_i386.deb
boinc-client_5.8.17-1_i386.deb
boinc-manager_5.8.17-1_i386.deb
gcc-4.2-base_4.2-20070502-0ubuntu2_i386.deb
libgcc1_4.2-20070502-0ubuntu2_i386.deb
libstdc++6_4.2-20070502-0ubuntu2_i386.deb

It appears that this new version will be in the repositories for Gutsy.  No idea if it will be backported for Fiesty.  This new version works very well here.

When I installed BOINC from the repos, it uses 5.4.11-5 (feisty), which works right out-of-the-box. No additional dependency issues involved.

The newer ones from the BOINC site have dependency issues which they warn you about prior to downloading. As such, if I don't use the repos, then I use version 5.4.11 from the BOINC site. The next stable release is 5.8.16, from BOINC.
The unstable version 5.9.5 I would not recommend as it could possibly crash and burn.

---

### Post by eapache on 2007-05-13
I'll try the new version, but it turns out that it isn't really a bug. I was running Rosetta, and it turns out that Rosetta just doesn't checkpoint very often at all. SInce I have a slow PC (P3 1Ghz), it took so long to reach the first checkpoint that it was never on for a long enough period of time. I've switched to some projects with smaller WU, and it's working fine with them.

---

### Post by TransitMan on 2007-05-13
The slower CPU's will lag greatly from todays' faster processors.
Glad you got it figured out.
And I learned something about the Rosetta WU's today that I did not know. Thanks.

---

