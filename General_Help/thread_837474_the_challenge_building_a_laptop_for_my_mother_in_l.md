---
title: "the challenge: building a laptop for my mother in law with alzheimer's"
date: 2008-06-22
forum: General Help
---

### Post by waynefoutz on 2008-06-22
Can someone please tell me if I'm on the right track. I have a mother-in-law that recently came down with alzheimer's and we had to put her in a nursing home. She is/was slightly computer literate, especially when it came to windows. She is not allowed to have her desktop computer in the nursing home, nothing larger than a laptop. The computer she was using was a total mess. Windows drivers were deleted, wrong drivers reinstalled, key system files removed, etc. Apparently, she had some sort of problem and tried to fix it herself, but her disease wouldn't let her. We are buying her a laptop, to conform to the home's rules. The problem is, I need it tamper proof. 
 I'm leaning toward Kubuntu, one because it resembles windows somewhat, considering everytime she sits in front of it it will be like a new computer for her, and two, because of the large amount of open source games and programs available. Her main use for this laptop will be light gaming, mainly arcade games like supermario clones, breakout type games,tetris clones, and watching dvd's. Internet access will not be available to her, because she started getting in the habit of buying things on the internet, sometime the same item a dozen times during the span of a week. 
 I've used ubuntu before, back when it was still in version 6, and I was impressed with it. My question is, will kubuntu allow me to keep her from opening konquerer and deleting system files? 
I need a tamper proof, easy to use OS to put on this laptop, any suggestions?

---

### Post by knutschr on 2008-06-22
I like Kubuntu the best, but I think you should install Ubuntu as that is made to do things easy without 'too many' options, as you  (for many) have in Kubuntu.

Draw the upper bar down, and add the things being in the other bar, there.
Then delete the other bar.

It will look like Windows.

Also make Gnome to remember after restart.

---

### Post by Zorael on 2008-06-22
I like Kubuntu the best, as I find it offers a more intuitive interface and generally feels more fleshed-out. Opinion: "Looking like Windows" doesn't enter into the equation at all, I'd say. It's just that stuff is where you expect them to be.

As long as she isn't root, she can't delete any system files whatsoever. You can make sure her user isn't a sudoer too. If you want to really go the extra mile, modify your grub menu.lst to lock alternatives (read: recovery mode) and lock the configuration, requiring that a password be entered.

She *will* be able to delete her own configuration files, in her user directory. All important ones are regenerated if deleted, but that still equates to settings lost.

---

### Post by waynefoutz on 2008-06-22
> **knutschr said:**
> I like Kubuntu the best, but I think you should install Ubuntu as that is made to do things easy without 'too many' options, as you  (for many) have in Kubuntu.

Draw the upper bar down, and add the things being in the other bar, there.
Then delete the other bar.

It will look like Windows.

Also make Gnome to remember after restart.

that's a good suggestion, thanks. I could just use the "applications" menu and omit the "places" and "system" menus. thanks! I hadn't thought of that approach.

---

### Post by waynefoutz on 2008-06-22
> **Zorael said:**
> I like Kubuntu the best, as I find it offers a more intuitive interface and generally feels more fleshed-out. Opinion: "Looking like Windows" doesn't enter into the equation at all, I'd say. It's just that stuff is where you expect them to be.

As long as she isn't root, she can't delete any system files whatsoever. You can make sure her user isn't a sudoer too. If you want to really go the extra mile, modify your grub menu.lst to lock alternatives (read: recovery mode) and lock the configuration, requiring that a password be entered.

She *will* be able to delete her own configuration files, in her user directory. All important ones are regenerated if deleted, but that still equates to settings lost.

looking like windows is pretty important actually. She will expect the "start" menu to be in the bottom left hand corner. You have to remember, learning something new for her is impossible, because she can't retain it. So each time she sits down it will have to look and behave in a familiar way. passwords aren't possible either. So her using the sudo function won't be a problem. It will have to be able to boot directly to the desktop, have a simple menu to the games and programs I install for her, and play dvd's automatically when she puts them in the drive. 
 I have no experience with kubuntu, limited experience with ubuntu and the gnome interface. I guess I'll try out kubuntu and see what it can do. 
 My main concern is her deleting things, breaking the install. She has a history of doing that with windows. The problem is, she knows her way around windows, because she worked in an office before her affliction. Now all that knowledge does is cause my wife headaches, because she's the one that gets the call in the middle of the night because the computer is broken.

---

