---
title: "Nautilus and Dolphin: Slow Network Browsing"
date: 2015-03-21
forum: General Help
---

### Post by marcus.pearlman on 2015-03-21
Hi All,

Nautilus and Dolphin are extremely slow when browsing network shares. I commonly view network hard drives that are on another network at physically far location, and browsing these shares using these file managers is so slow it is unusable. I mount the sshfs and cifs drives using fstab. Browsing the mount using terminal is fine and quick, and is how I do it now, but I really want to be able to use a gui file manager. 

Is there any way to speed up these managers or can someone suggest an alternative file manager to use to browse these shares and be able to drag and drop files to and from the shares?

I believe the reason it is so slow is because the file managers try to get information about the files such as size, number of files, etc. I messed with some preferences at "Edit -> Preferences -> Preview" but nothing helped. 

I did google search this issue but am having trouble finding forums on the subject. Please help, Thanks.

---

### Post by marcus.pearlman on 2015-03-23
I respectfully bump this thread.

---

### Post by SeijiSensei on 2015-03-23
I can browse shares on my remote server (across the country in California) in Dolphin using the fish:// protocol with only minor delays.  Usually it takes a second or two at the beginning to authenticate and generate the list of files, but after that it's only slightly slower than browsing shares on my local server.  Enter "fish://user@server/share/" in the address bar in Dolphin.  Does that work any better for you?

---

### Post by marcus.pearlman on 2015-03-24
Thanks Seiji! So I had a brain fart before, I have tried Nautilus and Nemo, NOT Dolphin. Both of those suck, but they look pretty. I just installed Dolphin to try and it is fast right out of the box! I did not try the fish protocol, but I did browse my mounted drives and it was seamless! I still need to try at my home where browsing these shares has even more of a problem than browsing at my work. 

Now I just need to learn how to use Dolphin. For example getting the sshfs entries in fstab to show up in the bookmarks column. The cifs entries show up under devices, but not my sshfs shares. Is fish the only way to be able to mount these drives from within dolphin? I'm looking into this right now, but feel free to answer if you know it. Thanks again.

---

### Post by marcus.pearlman on 2015-03-24
Dolphin seems to do its job well: file managing fast. The other details are not so easy, at least in Ubuntu. To fully convert to using dolphin as the default I need to solve a number of problems: dropbox indicator, svn context menu, dark theme bug (it has white text on whit background if I open new tab), be able to mount sshfs fstab entries from within dolphin (I never auto mount these entries, I always like to only mount them when I use them), and I think thats it.  I think my solution for now is to use Nemo as the default, and only use dolphin when browsing network shares. Maybe over time ill figure out these problems and make the switch.  Thanks again.

---

### Post by SeijiSensei on 2015-03-24
Don't the unmounted items in fstab appear in the left-hand panel of Dolphin?  I mount all remote shares at boot so I can't be sure.  Why are you averse to mounting shares at boot? It's certainly a lot more convenient and no less secure.

You can create a link to a folder in Dolphin by dragging the folder icon into the left-hand panel.

---

### Post by marcus.pearlman on 2015-04-02
> [COLOR=#000000]Don't the unmounted items in fstab appear in the left-hand panel of Dolphin?[/COLOR]
Only the unmounted cifs items show in dolphin. The sshfs items do not show up.  Even after I mount the sshfs ones, they still are unavailable in the Dolphin side panel. I'm sure there is a fix, but I haven't looked. Do you have any sshfs shares?

> [COLOR=#000000] Why are you averse to mounting shares at boot?[/COLOR]
Some of my shares require a vpn. I only use vpn when I am working to get work files and such. If I am not working, and I am not connected to vpn, I definitely do not want to auto mount these shares. This is a reason we both can agree on, this next reason is a preference. I am not sure the computational 'cost' of having shares mounted. Probably not much; however I just have a minimalist philosophy of only use what you need. Old habits die hard I guess, and it isn't that hard to just quickly mount the drives when it is on the side panel of file managers.

But just to reiterate, dolphin is very fast for browsing these outside network shares. I tried it at my home, and now I do notice a delay, but it is less than a second. Much better than a >minute delay from Nautilus and Nemo. I use Dolphin a lot now, and am considering to put the time in to solving these few problems to make the full switch.

---

