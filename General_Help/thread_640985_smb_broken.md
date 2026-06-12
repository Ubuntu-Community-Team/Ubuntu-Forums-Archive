---
title: "smb broken"
date: 2007-12-14
forum: General Help
---

### Post by onesojourner on 2007-12-14
Networking, sharing folders specifically has become totally unreliable (actually its unusable) in the past month on my desktop. My laptop also is behaving strangely. When it is working properly I can click places > networking and I can see my desktop, my laptop and windows network. Lately when I click on networking it takes about 45 seconds to load and then it only displays windows network witch incorrectly displays nothing. I have several windows (samba) shares on both computers. About 10% of the time it will display correctly and then the network is going extremely slow. It wont even stream a basic SD video file. There is no telling when it will be not working at all or when it will be slow. I have tried restarting refreshing and every other little thing I could think of but the behaviour is totally random. I have made no changes to the system in several months other than installing the updates as they come. both laptop and desktop are wireless going to a dd-wrt router.

---

### Post by dummyhead3 on 2007-12-14
Are you sure that you have samba installed?

---

### Post by onesojourner on 2007-12-15
yes. Everything was working fine up until about a month ago. Since it is happening on both computers could it be a router issue? I have a wrt54g with dd-wrt installed but all the settings are stock other than wep. The only thing I can figure out is maybe one of the newer updates messed things up.

---

### Post by jetsam on 2007-12-15
It's possible you have an obscure bug that some people have reported with the latest Samba security update. Do you have a Gutsy live cd? If you boot it and can browse the network from the live cd, then you probably have the bug.

One possible solution, if you do have the bug, is in my post, the third in this thread: [http://ubuntuforums.org/showthread.php?t=626861](http://ubuntuforums.org/showthread.php?t=626861)

Other people have been able to work around this issue by putting smb://*windows_ip_address* in the location bar in Nautilus.  Replace *windows_ip_address* with the ip address of the computer you are trying to browse.

---

