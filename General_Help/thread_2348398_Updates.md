---
title: "Updates"
date: 2017-01-03
forum: General Help
---

### Post by gwahyyr on 2017-01-03
Hey guys, 

 I've been wondering about an issue that concerns the upgrade process through the terminal. After running the "sudo apt full-upgrade" command, I always get the following feedback during the upgrade.: " some metadata was ignored due to errors". The machine runs smoothly nevertheless, just wondering if receiving this message is something common or not?

---

### Post by lisati on 2017-01-03
*Thread moved to **General Help**.* from [https://ubuntuforums.org/showthread.php?t=2348311](https://ubuntuforums.org/showthread.php?t=2348311)
Please do not hijack threads with unrelated questions.

---

### Post by deadflowr on 2017-01-03
Does the error mention appstream?

---

### Post by gwahyyr on 2017-01-05
I entered my question to a thread relating to the use of the terminal, hence I saw no use in opening a new thread for a single question. I do not understand your use of the term "hijack" in this context. Can you please explain so I do not "hijack" again in the future?

> **deadflowr said:**
> Does the error mention appstream?

I'm not sure, but I will check during the next upgrade.

---

### Post by howefield on 2017-01-05
> **gwahyyr said:**
> I entered my question to a thread relating to the use of the terminal, hence I saw no use in opening a new thread for a single question. I do not understand your use of the term "hijack" in this context. Can you please explain so I do not "hijack" again in the future?.

You asked a completely unrelated question in a thread belonging to someone else, you added nothing to that posters thread other than confusion by asking others to answer your quite different question as well as the thread creators question, this is considered rude and a "hijack" of the original posters thread. Don't do it, it is always better to start your own thread.

---

### Post by gwahyyr on 2017-01-07
> **howefield said:**
> You asked a completely unrelated question in a thread belonging to someone else, you added nothing to that posters thread other than confusion by asking others to answer your quite different question as well as the thread creators question, this is considered rude and a "hijack" of the original posters thread. Don't do it, it is always better to start your own thread.

No disrespect intended, my apologies. Thank you for clarification.

---

### Post by gwahyyr on 2017-01-12
> **deadflowr said:**
> Does the error mention appstream?

Indeed, the full message is as follows: "AppStream cache update completed, but some metadata was ignored due to errors."

This message comes up at the very end of the update process with "sudo apt update".

---

### Post by deadflowr on 2017-01-12
Their is a fix for it
First you must make sure that Backports are enabled:

Go to Software and Updates and in Updates make sure the Unsupported Updates is checked.
(Or edit your sources.list directly and make sure the backports line is uncommented (uncommented are lines without a # in the front, lines with a # are not read by the system)

Then in a terminal run:
```
sudo apt install appstream/xenial-backports
```
then when that is done run:
```
sudo appstreamcli refresh --force 
```

that should so it.

Of course, this applies to xenial (16.04)
but I have not heard or seen any reference of this error for any other release (16.10?)

---

### Post by gwahyyr on 2017-01-21
> **deadflowr said:**
> Their is a fix for it
First you must make sure that Backports are enabled:

Go to Software and Updates and in Updates make sure the Unsupported Updates is checked.
(Or edit your sources.list directly and make sure the backports line is uncommented (uncommented are lines without a # in the front, lines with a # are not read by the system)

Then in a terminal run:
```
sudo apt install appstream/xenial-backports
```
then when that is done run:
```
sudo appstreamcli refresh --force 
```

that should so it.

Of course, this applies to xenial (16.04)
but I have not heard or seen any reference of this error for any other release (16.10?)

I've performed the recommended commands succesfully, thank you for your detailed response. I'M using xenial, not sure if this ever occured in 16.10.

---

