---
title: "terminal typing problem"
date: 2008-04-28
forum: General Help
---

### Post by sirdrakey on 2008-04-28
just converted to ubuntu and was adding things i need like wine compiz and samba everything loaded with no hicup but i went to edit the samba settings as talked about in [http://www.debuntu.org/guest-file-sharing-with-samba]("http://www.debuntu.org/guest-file-sharing-with-samba")

but for sum reason i cannot type g[ or some other keys that are needed for the changes and the arrows keys spell out abcd for some reason. with any hope there is a reasonable explanation

i thought maybe it was a keyboard issue but the keyboard works fine in notepad. So it must be a terminal problem or a pebkac :(

any help I thank you now

---

### Post by Monicker on 2008-04-28
> **sirdrakey said:**
> just converted to ubuntu and was adding things i need like wine compiz and samba everything loaded with no hicup but i went to edit the samba settings as talked about in [http://www.debuntu.org/guest-file-sharing-with-samba]("http://www.debuntu.org/guest-file-sharing-with-samba")

but for sum reason i cannot type g[ or some other keys that are needed for the changes and the arrows keys spell out abcd for some reason. with any hope there is a reasonable explanation

i thought maybe it was a keyboard issue but the keyboard works fine in notepad. So it must be a terminal problem or a pebkac :(

any help I thank you now

Those instructions tell you to open the file with the vi text editor.  If you have never used it before, it can be quite a challenge.

As much as I love vi/vim myself, I would recommend that you edit the file this way:

```
gksudo gedit /etc/samba/smb.conf
```

or even this, if you don't mind being at the command line:

```
sudo nano /etc/samba/smb.conf
```

---

### Post by sirdrakey on 2008-04-29
thanks i was going out of my mind! my first comp was a trs-80 so i have good times with command line. 

i didn't know the vi was an editor so i was hitting the wall the nano worked. Later i'll learn vi but i just want my comp to talk with it's friends again on my network.

looks like it sees them and they see him but still having some permission problems on windows side i will walk thur the code to see if i missed something and when i edit will use nano 

thanks Monicker

---

