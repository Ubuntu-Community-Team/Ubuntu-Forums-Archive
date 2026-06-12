---
title: "Upgrade 70 8.04 or fresh install"
date: 2008-04-24
forum: General Help
---

### Post by randomAccess on 2008-04-24
While 8.04 was in beta, I tried to upgrade the system and after the upgrade I could not get into the GUI. After login prompt, X error would appear, and I was back to login prompt. I didn't write down the message so I don't know which error it was.

Now, 8.04 is stable and I am afraid to upgrade it. The problem with upgrade is that 
1. Will Compiz work well after the upgrade? I know that Compiz' new version does not follow new ubuntu versions.

2. During the upgrade, I always get the message should Ubuntu overwrite some existing config files. I suspect that this may be the reason why every Ubuntu crashed after the upgrade. What do you do with such messages?

3. Linux is the only system I have so I cannot risk that it crashes and destroy all config files. 

4. After clean install (reinstall), will I lose config files if they are placed on a separate /home partition? I think it happened to me in the past.

---

### Post by notwen on 2008-04-24
> **randomAccess said:**
> 4. After clean install (reinstall), will I lose config files if they are placed on a separate /home partition? I think it happened to me in the past.

As long as you don't format your /home partition your config files will remain intact.  I personally prefer to do clean installs over upgrades, simply to avoid any additional conflicts caused by certain packages I manually compiled.  Just be sure to backup all of your needed data before hand.  After the install you would need to go back and re-install your previous applications for their config files to serve their purpose, you may also want to verify these config files work w/ any of the newer versions of their apps that may be included in the new version of Ubuntu.  Hope this helps.  =]

---

### Post by randomAccess on 2008-04-24
Just to make it clear as I didn't test this.

Config files will remain on /home and reinstalling application WILL NOT overwrite them, but USE them???
Is the same with packages that needs to be recompiled?

---

