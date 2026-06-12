---
title: "Moving Dropbox folder to SD Memory"
date: 2015-03-25
forum: General Help
---

### Post by alex355 on 2015-03-25
Good morning,

I have a laptop with 24Giga SSD (where Ubuntu is installed) and 750Giga HD (where Win is installed).

Ubuntu works perfectly, but I need to use Dropbox for work and in order to synchronize it requires an amount of free space that should be twice the size of Dropbox folder.

So, my SSD is full and Dropbox doesn't synchronize anymore.

I bought a 32G SD Memory to move my "Dropbox folder" there, so it can have all the space to synchronize without affecting my SSD, but when in Dropbox preferences I try to change the position of "Dropbox folder" from SSD to SD, it says there's an error like: "Some files can't be moved. Select another position or close open files and try again".

Of course there's no open file, it's a problem of destination as I read it's almost impossible to move that "Dropbox folder" on a SSD card.

If someone has a good solution for this problem I will be forever thankful :)

Sorry for my description, I'm quite a beginner.

Thanks a lot for attention.

---

### Post by nerdtron on 2015-03-25
I'm no longer using dropbox but worth a try.

Uninstall dropbox.
Copy all dropbox files to the new folder you want.
Re-install dropbox, it will ask you where to save your dropbox folder.
Point it to the new folder.
Let it sync.

---

### Post by Vladlenin5000 on 2015-03-25
> **nerdtron said:**
> I'm no longer using dropbox but worth a try.

Uninstall dropbox.
Copy all dropbox files to the new folder you want.
Re-install dropbox, it will ask you where to save your dropbox folder.
Point it to the new folder.
Let it sync.

This should work, of course, but deleting the hidden *.dropbox* folder should be enough. This is where the account and client settings are stored. Deleting it will force the client to recreate it as soon as you open Dropbox. It'll take to the same initial setup wizard where you login with your account and then choose/point it to new folder (do not accept the default options).

---

