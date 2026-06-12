---
title: "Why is dual boot slow (Ubuntu + XP)?"
date: 2007-04-24
forum: General Help
---

### Post by g3nji on 2007-04-24
Hello everyone,

I installed Windows XP on my 80GB hard drive & C2D 1.8Ghz. Boot time into Windows was < 50 seconds. 

Then I installed Ubuntu 7.04. Loading into Ubuntu is less than 30 seconds.

But when I boot into Windows it takes 1 minute and 32 seconds. 

Is this normal?

Thank you for reading.

~Genji

---

### Post by bicchi on 2007-04-24
Your boot time into windows should not have changed. Once grub passes control to XP, it takes over your machine as if Ubuntu was not installed. Did your defrag your XP partition before installing Ubuntu? Hopefully its not related to data lost, but windows might have given you an error/warning message if that was the case.

Maybe windows had to readjust to the new partition size or rebuild some kind of database which made it take longer. Lets hope for the best. :)

---

### Post by g3nji on 2007-04-24
Thank you for your quick reply:) 

Yes I did run a defrag using Auslogics before the install. 

And you were thankfully right!

As soon as I read this I rebooted and Windows was just 3 seconds slower than normal -- but that

is okay. 

Thank you.

~Genji

---

