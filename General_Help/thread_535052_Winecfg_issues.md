---
title: "Winecfg issues"
date: 2007-08-26
forum: General Help
---

### Post by melzanis on 2007-08-26
Hey Everyone, 
        I'm know to Linux and have been trying to install wine so that I can use some programs from windows ( in short WoW). However, when I go to use "winecfg" I find that I can't get to the apply button due to this window that cuts off the button of the "winecfg" window.  I'm just wondering how to I resize this window because it's really starting to bug me =P.

Ok nvm I just fixed it... 

However I it seems that I can't a problem in creating the "C:\" directory. The following is the print out:

err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\Desktop".
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0
err:winecfg:load_drives GetVolumeInformation() for 'F:\' failed, setting serial to 0
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\My Documents".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\My Pictures".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\My Music".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\My Video".
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\My Documents".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\My Pictures".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\My Music".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\My Video".
fixme:msg:pack_message msg 14 (WM_ERASEBKGND) not supported yet
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\Desktop".
err:shell:SHGetFolderPathW Failed to create directory L"c:\\windows\\profiles\\warlock\\Desktop".
 
can anyone tell me how to fix this please.

---

### Post by TeaSwigger on 2007-08-26
Hello,

Try moving the pointer about at the bottom right of that window. You should be able to drag the frame to bare the button (gasp! what is he talking about?).

Or if for some odd reason you can't get it to change, perhaps go to settings and window manager. In there, pick a different "theme" for the windows and see if that doesn't change it to something you can get to work. Just guessing from the description, maybe I'm misunderstanding... but good luck :)

---

