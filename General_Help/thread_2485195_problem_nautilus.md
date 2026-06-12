---
title: "problem nautilus"
date: 2023-03-22
forum: General Help
---

### Post by jgw on 2023-03-22
I have a problem with nautilus.  Its pretty simple and I suspect I should know how to fix this one.  My problem is when I try to delete a character, or group of characters from the front the del key becomes a period key, and press the del key I get a period.  The only way to delete is from the back.  Perhaps my mind is slipping but I don't think this is right.

Thank you.................

---

### Post by Claus7 on 2023-03-24
Hello,

is this in the renaming process of a file or folder? Which version of nautilus? I cannot replicate your issue under 22.10.

Regards!

---

### Post by jgw on 2023-03-24
Thank you for the reply!

Here is what I have done in my quest so far.  I have run "sudo apt-get install --reinstall nautilus"  which, in theory, installed the latest and greatest.  Seemed to do the deed with no errors. Would check the version but have no idea how. 

I checked to see if I still have the problem - I do.  I entered sss then moved to the second 's' and pressed del and got s.ss so its still doing it.  With the new one I find that my 'del' key is now another key for '.' (doesn't matter where)

---

### Post by Claus7 on 2023-03-24
Hello,

for the version you could open nautilus and from the sandwich button on the top right pick up "About Files": this will tell you the version of it. I think that something got messed with your keyboard instead of Files, since it does not matter where '.' is shown when del is pressed. 

Ideas: 
1) Under settings -> keyboard -> view and customize shortcuts -> mainly custom shortcuts: have you added anyone by accident and you see such a behavior?
2) again under settings -> keyboard, yet now -> input sources: are you sure you have picked up or not messed the preferred keyboard for your system?

Regards!

---

### Post by jgw on 2023-03-27
Thank you for the reply!

The keyboard is not at fault for the period.  I have tried it on a different machine and it works just fine.  I have to check the keyboard setting.

---

### Post by jgw on 2023-03-29
I thought I had fessed up on this one.  its embarrassing. 

The entire problem was in the keyboard.  The answer was to turn off the Num Lock.  

Thank you for the help - I will mark this as solved.

---

