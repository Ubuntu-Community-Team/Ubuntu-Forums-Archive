---
title: "Help recovering data, faster way to check drive passwords needed"
date: 2014-07-17
forum: General Help
---

### Post by Will1134 on 2014-07-17
Here's the situation I'm in. I have a chunk of data I've been keeping for years and moving from computer to computer. I had a few hard drive failures which led to there being only one copy of the data being on an external drive. I was in the process of transferring it to my laptop when it got bumped and now the drive clicks. It was an absurdly light bump that left me a little devastated though I had already got the most important files out. This drive has been sitting for years hoping I can repair it somehow.


Just recently I've discovered one of my other corrupted hard drives that contained that data. I think I've managed to repair the drive sectors though the drive is encrypted. This is when I was just playing with the encryption features so I wasn't taking it too seriously about recording the keys and the passphrase though I suspect that much of my missing data may be on it. 


I have an idea what the drive encryption key is though I've tried it and it has not worked. I also have an idea of what the password to the drive is but it was years ago and I only remember what it might be or that it's a permutation of a password I normally use. 


So here's the question, I've been trying to figure it out though in order to test one password I have to search the entire drive for encrypted volumes, find it, make the right choices (because there are two encrypted volumes on it), test the password and when it doesn't work, spend a lot of time searching the drive for the partition again and repeating the process. I want to know if there is a faster way I can test these passwords or if I can even brute force it, because I suspect I made the login password really short.   I was just testing and playing with this drive after all and didn't need to really encrypt this data on my home computer. Now that this drive might be the key to getting my data back I wish I took it more seriously!

I've been just following guides online to get this far. I'm not sure if my attempts to fix the drive using the usual recovery tools may have ruined the data or not.

So long story short, I'm sure I don't know the long, 32 character mount passphrase as I've tried all the ones I've recorded, but I'm sure I can guess the wrapped passphrase (If I have my terminology right) given enough time or a few moments brute forcing it (since I'm sure it's short 3-4 characters long)

Here is a bit of the log of me trying to recover the drive data:

```

will@6wire:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/will/f09013ce-c921-467b-b7b3-29c722cb4f79/.ecryptfs/hr/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
will@6wire:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/will/f09013ce-c921-467b-b7b3-29c722cb4f79/.ecryptfs/hr/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
will@6wire:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/will/f09013ce-c921-467b-b7b3-29c722cb4f79/.ecryptfs/hr/.Private].
Try to recover this directory? [Y/n]: n
INFO: Found [/media/will/f09013ce-c921-467b-b7b3-29c722cb4f79/.ecryptfs/will/.Private].
Try to recover this directory? [Y/n]: n

```

Thanks for any help that can be offered!

---

### Post by steeldriver on 2014-07-17
it should be possible to specify the previously found directory as a command line argument, no? e.g.

```

sudo ecryptfs-recover-private  /media/will/f09013ce-c921-467b-b7b3-29c722cb4f79/.ecryptfs/hr/.Private

```

The filesystem search should only happen if it's invoked with no argument, I think

---

### Post by Will1134 on 2014-07-17
Thanks for the probably good solution to what I want. Though currently the computer won't turn on.

Back at you soon I hope!

---

### Post by Will1134 on 2014-07-17
I've gotten it working and that does work. So far no luck guessing it. Is there a brute force script I can use somewhere?

---

### Post by sedawk on 2014-07-17
First make a backup of .ecryptfs/wrapped-passphrase to another place. e.g.
cp /media/will/SEEABOVE/.ecryptfs/wrapped-passphrase /dev/shm/testme.bin
(make a permanent backup to your home directory too!)
Now you can run tests with the copy at /dev/shm/testme.bin:
ecryptfs-unwrap-passphrase /dev/shm/testme.bin 
It asks for "passphrase" but what it really means is your old login password.
If you provide the correct old login password, it will print the "real" passphrase of ecryptfs.
(actually it looks like ecryptfs is always asking for the (old) login password and never for the real passphrase.
 So what you are actually missing above is your old login password, not the passphrase of ecryptfs.
 The terminology of ecryptfs is really broken ...).

To run a brute force attack against "ecryptfs-unwrap-passphrase /dev/shm/testme.bin" you need a string generator
(permutations, dictionary, incremental word generator) and the tool "expect" and some script magic.

---

### Post by Will1134 on 2014-07-17
Turns out I didn't need to brute force it, enough trial and error got it eventually. Turns out it was a password I haven't used in a very long time. Thanks for the help! I found the important stuff I wish I could have recovered! Very happy

---

