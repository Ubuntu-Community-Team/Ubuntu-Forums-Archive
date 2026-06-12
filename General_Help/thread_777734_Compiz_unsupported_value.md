---
title: "Compiz unsupported value?"
date: 2008-05-01
forum: General Help
---

### Post by LeoSolaris on 2008-05-01
I was puttering around and moving a file from my desktop to a folder in Pictures, when compiz suddenly ceased. I figured it was just a crash, since I am using 8.04, so I restarted it with terminal. This is what I got as an output.

```
03:28:32 on Thu May 01 - leo:~$compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/widget/allscreens/options/toggle_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/shift/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/shift/allscreens/options/initiate_all_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

Should I worry about these unsupported values? If I should worry, where am I headed to change them, and what should they be? I had never started compiz from terminal before, so I am not completely sure what I am really seeing here.

Thanks!
Leo

---

### Post by x86macro on 2008-05-01
when i first installed compiz i got that same error but i've ignored it 100% because the path to the file it is referring to doesn't appear to exist (i'm new to linux though so i'm sure i'm missing something).  anyways, i've had no issues with compiz.  when i bust the $compiz --replace at the command line i get that same output.  then i close the terminal (which doesn't return to a prompt), the window borders dissappear and reappear...and compiz works perfectly.

so i vote for not worrying about it.  since you said you hadn't started it from a prompt before then it's likely this error was already there.

---

### Post by LeoSolaris on 2008-05-04
> **x86macro said:**
> when i first installed compiz i got that same error but i've ignored it 100% because the path to the file it is referring to doesn't appear to exist (i'm new to linux though so i'm sure i'm missing something).  anyways, i've had no issues with compiz.  when i bust the $compiz --replace at the command line i get that same output.  then i close the terminal (which doesn't return to a prompt), the window borders dissappear and reappear...and compiz works perfectly.

so i vote for not worrying about it.  since you said you hadn't started it from a prompt before then it's likely this error was already there.

Thanks mac. I opted for that and gave it a couple of days. After a little while, I did go in and turn off the switch and scale plugins because I never use them. I think the remaining one is because I swapped the keyboard shortcut for my widget layer to the menu key that is right next to my left arrow. It was already taken to open menus on the normal keyboard layout, but so far it still works.

Leo

---

