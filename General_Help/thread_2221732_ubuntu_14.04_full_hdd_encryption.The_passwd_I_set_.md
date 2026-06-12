---
title: "ubuntu 14.04 full hdd encryption.The passwd I set wont work.Error?"
date: 2014-05-03
forum: General Help
---

### Post by ubto66 on 2014-05-03
Ubuntu 14.04 64bit

It is about the full hdd encryptionoption when installing.
On previous ubuntu versions I have usedalternate images. So I know about the full hdd
encryption procedure.


The downloaded ubuntu 14.04 iso Isha256sum checked. 
I burned the iso to dvd using brasero,and set a sha256sum verification. 
I then installed ubuntu 14.04 andchecked full hdd encryption.
I set a strong password, which ubuntu14.04 verified with a
green check mark.
I did not have internet connectionduring installation. Let me know if that is of
importance?
During all this, there was no errormessages.


When I start ubuntu 14.04 I get theenter the password screen picture.
When I enter the password, I get awrong password message. After entering 3 times, ubuntu
jumps out and displays
'gave up waiting fo root device commonproblems
boot args
check rootdelay
check root 
missing modules
Alert /dev/mapper/ubuntu -vg root doesnot exist
Busybox v.1.21.1
(initramfs)-'


Does this tell you anything?


Of course I could be entering the wrongpassword, so I installed again. This time even more focused
on setting the password and enteringthe password correctly when starting ubuntu 14.04.
Same result.


Then I installed a 3. time. This time Iset a one letter full hdd encryption password.
Started ubuntu and entered the shortpassword. And ubuntu 14.04 ran without errors.


Because you cannot see what you arewriting, when you set the full hdd encryption password,
I cannot say, that I both timesset the password I wanted. But I believe it is likely that
I got it right one of the times.


My question is, is there a bug or errorwhen you set a long full hdd encryption password?


Else, how do I get the setting of thepassword right?
Like I mentioned, I have installedubuntu 12.04 alternate with full hdd encryption again and
again. I do not think, I haveexperienced getting it wrong before.


Thanks.

---

### Post by ubto66 on 2014-05-10
The problem mayoccur if you select one language as your system language and anotherlanguage as your keyboard layout language.


Fx if you choose english as your systemlanguage and a non english language, which I did, as your keyboardlayout language then when you create the full hdd encryptionpassword, ubuntu 14.04 will use the english keyboard layout language,and not the keyboard layout language you selected.


But when you restart the computer afterinstalling ubuntu 14.04, it will prompt you for the full hddencryption password, and now use the keyboard layout language youselected during the installing of ubuntu.


This difference may result in you notbeing able to enter the password correctly.

---

