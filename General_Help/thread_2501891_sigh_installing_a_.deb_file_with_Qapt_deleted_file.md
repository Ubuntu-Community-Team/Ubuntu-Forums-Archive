---
title: "*sigh* installing a .deb file with Qapt deleted files"
date: 2024-10-25
forum: General Help
---

### Post by justsomeguyinslc on 2024-10-25
I was installing a .deb using Qapt (Kubuntu 24.04.1) and before I realized it for some reason, this damn app decided to delete a boatload of packages, including a hefty chunk of system files. All I can do now is boot to command line. I have no network. I am really trying to avoid doing a fresh install of the OS, but at minimum I need to move files onto a USB key. But, I'd rather find a way to fix the filesystem. I have Timeshift backups but I can't run Timeshift at the cli since so many filesystem packages were deleted. 

I've tried everything I can think of, but I am now at hair tearing-out status. Does anyone have any thoughts? Please?

Thanks.

--Tony

---

### Post by TenPlus1 on 2024-10-25
What was the .deb you installed, and which files were listed for removal ?

Maybe you could do a "sudo apt install kubuntu-desktop" in terminal to bring reinstall the base.

---

### Post by Tadaen_Sylvermane on 2024-10-25
> I've tried everything I can think of, but I am now at hair tearing-out status. Does anyone have any thoughts? Please?

Random debs are not safe just because they are deb files. Don't do it again. Put it in distrobox or something next time. You can check your /var/log/apt/history file to find what was removed but it will likely be easier to just reinstall. If it's to the point that you can't even run cli timeshift to restore then you very likely can't just "fix" it without a ton of methodical slow manual intervention. Reinstall and learn from it is likely the best course of action.

One thing that you can do with timeshift is load into a live environment then mount your timeshift drive and restore the partitions that way. That can be finicky though as there are more manual steps involved if you format the partitions first, which I highly recommend as you have no clue what files were removed and which were flat out replaced.

> this damn app decided to delete a boatload of packages, including a hefty chunk of system files

Don't blame the app. It is just a frontend for apt. Blame the random ass .deb package you downloaded as Qapt just followed the specifications in the .deb file and nothing more. This is not a Qapt issue.

---

