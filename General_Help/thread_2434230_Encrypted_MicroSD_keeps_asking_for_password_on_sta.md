---
title: "Encrypted MicroSD keeps asking for password on start up"
date: 2020-01-02
forum: General Help
---

### Post by ahwbacon on 2020-01-02
I'm new to Ubuntu (actually using Lubuntu).

I have an old Asus laptop and Lubuntu runs really well. Fast.

I have a MicroSD card (256GB) which I formatted using KDE partition manager, there was an option to encrypt, so I did.

Every time I start Lubuntu a box appears asking for the password, theres an option to Remember. When I click this I'm expecting Lubuntu to automatically unlock this drive when logging on but it doesnt, instead it keeps prompting me to log in along with the option to remember. When entering the password I can access the drive.

Any ideas?

Might be linked...
When I first created the encrypted MicroSD I couldnt wrtie to the path, I had to run the below (or something similar, took a while to figure out, but after running I could write). I wonder if my issue above is linked to this other issue I experienced? I would have expected that when I formatted, encrypted the user that done that task would have full access/control but seems it doesnt.

[B]sudo chown -R yourUserName /media/mount_point



[/B]

---

### Post by TheFu on 2020-01-02
If you don't want to be bothered, don't have the MicroSD card inserted.

I don't have Lubuntu, so can't check out the details.  Sorry, don't know anything about "Remember" ... that would defeat the purpose of using encrypted storage, IMHO.  If I didn't actually want it to be non-trivial to access, then I'd use normal Unix permissions to prevent other users access.  **chmod 770 /path/to/directory** would be the way, making normal assumptions. Those assumptions might not be true for your situation.

Which file system did you choose for the SD card?  f2fs or something not flash storage friendly?

What type of encryption is being used?  Something not recommended like encryptfs or encfs?  Or perhaps DM+LUKS?  With LUKS, you can use an external device/file to decrypt.  I wouldn't want it to be automatic, but that's me.  For my encrypted storage, I find a yubikey with challenge-response to be a nice trade off.   LUKS has 8 slots to allow different methods or users to be used to open the encryption container.

---

### Post by ahwbacon on 2020-01-03
Hi. Im using an ASUS Netbook has 30GB SSD (Windows 10 uses all that space hence the jump to linux) With Linux I now have 20GB free. The SD card is 256GB for movies, documents etc hence I want to use it. Anyway I tried out some other distros, now using Mint which is actually really good, and just as fast as Lubuntu on my netbook (which isnt fast). When I click remember on mint it remembers, so it must be a lubuntu thing as its not an issue on Mint. The reason I want it encrypted is if my laptops lost anyone can use the micro SD, but with encryption they cant. The fact that it auto unlocks when I log in is ok, as they must bypass the encrypted Min instance.

---

### Post by TheFu on 2020-01-03
Ah .... Mint is using the old-style, less secure, HOME directory encryption, almost certainly.  This is method is fine for non-state actors, but leaks metadata.  Ubuntu removed the HOME directory encryption for a number of reasons. You can look those up and make your own decision.  Getting other tools to expect less-secure encryption will be an uphill battle, if my guesses are correct.

Is there a .private/ directory in your HOME?

---

