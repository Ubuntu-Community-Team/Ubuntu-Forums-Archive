---
title: "Default Terminal customization and alias not working on Ubuntu 22.10"
date: 2022-11-11
forum: General Help
---

### Post by Raging_Cascadoo on 2022-11-11
After installing Ubuntu 22.04 a few months ago, I noticed some differences via terminal. 

The colours no longer worked, like blue to display folders or green for executable scripts. 
TAB does not auto complete for commands or command suggestions but only worked for directories.
Alias like "ll" does not work.

I thought this may have been fixed in an update but that never happened. Around the same time I had created a VM with 22.04 for testing and noticed that the terminal had all these customization from the get go. I used it as is and assumed that maybe when upgrading to 22.10 it would have been resolved but the terminal remained the same even after the upgrade to 22.10.

I see that **.bashrc **is present on the VM but is missing on my bare metal installation. Is there an easy way to fix to this such as copying the **.bashrc** from the vm to bare metal?

---

### Post by &amp;KyT$0P# on 2022-11-11
> **Raging_Cascadoo said:**
> I see that **.bashrc **is present on the VM but is missing on my bare metal installation. Is there an easy way to fix to this such as copying the **.bashrc** from the vm to bare metal?

Yes that could be the solution.  In Ubuntu [FONT=Courier New]~/.bashrc[/FONT] is the default place for the setup of all of that stuff.

You might also be able to copy it from [FONT=Courier New]/etc/skel/.bashrc[/FONT] , but obviously that wouldn't get any customizations you made to that file in your VM, if there are any.

---

### Post by Raging_Cascadoo on 2022-11-11
I forgot about [FONT=Courier New]**/etc/skel/.bashrc**. When I checked this and compared to the .bashrc on the home folder on the VM, they were the same [/FONT]so I just copied [FONT=Courier New]**/etc/skel/.bashrc **to my home directory, restarted terminal and it now works. The 22.04 was a fresh installation and not an upgrade, so I am not sure how my user was created without the .bashrc against what was in skel but it works now, thanks![/FONT]

---

