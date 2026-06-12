---
title: "Tb Sharing Profile File On two Linux set-ups - Errors?"
date: 2007-06-26
forum: General Help
---

### Post by stevebakerj on 2007-06-26
I have salos posted this to - mozilla.support.thunderbird

Hi,

I have 2 Linux set-ups Kubuntu 7.04 Feisty and Kubuntu 7.10 Gusty Tribe 1 (same disk separate partitions)

I am running Tb 2.0.0.5pre and Tb 2.0.0.4 Release

I have a common Profile residing on a separate disk.

Feisty set-up has no problem with the profile residing elsewhere

Gusty set-up displays the following error on Tb .4 or .5pre starting:

"Could not initialize the Browser's security component. The most likely cause is problems with files in your Browser's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the browser and fix the problem. If you continue to use the browser session you might see incorrect browser behaviour when accessing the security features."

Also Any mail which is downloaded is suspected of having a virus??? I can not install or uninstall any Themes/Extension. My current theme thinks it is being used but the default Tb 2.0.x is. None of my other extensions load, but are clearly shown as installed in the Extension manager drop down.

Both Feisty and Gusty have the same read/write permissions to the profile drive, I have Fx 2.0.0.4 and 2.0.0.5pre sharing  a common profile on the separate drive with no issues. I have no issues with space on any of the drives I have more than 100 Gig spare on each drive

My console displays the following error message:

"[Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIFileOutputStream.init]" nsResult: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)" Location JSFrame :: File:///usr/lib/thunderbird/components/nsExtensionManager.js :: OpenSafeFileOutpputStream :: line 557" data: no]

My console displays the following messages:

"No Chrome package registered for chrome://moretools/skin/em-icon.png  ."    - For all of my extensions (several)

Any ideas/pointers as to what is going wrong???

All of my mail is intact an in the relevant mailbox, all of my filters are intact but unable to be applied

---

