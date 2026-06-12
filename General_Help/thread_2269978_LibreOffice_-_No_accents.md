---
title: "LibreOffice - No accents"
date: 2015-03-19
forum: General Help
---

### Post by kuckunniwi on 2015-03-19
Hi,

I'm writing 'cause of a strange phenomena (as far as I'm concerned) with Libreoffice. I'm using Kubuntu 14.04, in English, on a Spanish laptop (Spanish keyboard). Until now I've had no problems, but all of a sudden, none of the accent keys work: é, è, á, à, â, etc. This problem is exclusively occurring in Libreoffice, I have no such issue with any other software (Firefox, Thunderbird, etc.)

I've checked locale and language settings in Libreoffice writer, but it doesn't seem to change anything. Does anyone have any ideas of what the problem might be and what I can do to fix it?

Thanks a ton!

---

### Post by dino99 on 2015-03-19
is libreoffice been upgraded recently ? then you get that issue (maybe downgrade for testing)

---

### Post by amanchesterman on 2015-03-19
The standard advice is: "If you notice any strange behaviour in Libre Office ... the first thing to try is to reset the user profile."
Instructions are here: [https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)

---

### Post by kuckunniwi on 2015-03-25
Thanks to both of you for your replies.


> **amanchesterman said:**
> The standard advice is: "If you notice any strange behaviour in Libre Office ... the first thing to try is to reset the user profile."
Instructions are here: [https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)

I tried your suggestion, but it didn't fix anything. On the other hand, I've just began to notice some strange behaviour with accents and special characters on a system-wide basis: any files with accents or special characters in them, my system isn't able to open (a video in vlc), or give me a "file does not exist" error when trying to move or delete, which I can only do if I rename the file and remove the special character(s). On the other hand, I can input âll kïnds ôf spècíal chàráctèrs here in FF without any problems...

Not too sure what to do here, any further suggestions, at least to point me in the right direction, would be great! Thanks, guys!

---

### Post by kuckunniwi on 2015-05-26
If anyone could help me out with this, I'd be extremely grateful. I installed system-wide language translations for English, Spanish, French and Catalan (although I didn't have them before and I had no issues of this sort), but still no changes. Thunderbird won't let me save files to my filesystem unless I remove accents or special characters from file names, vlc won''t open videos unless I rename them, and I'mm finding myself having to use MS Word (wine) instead of Libreoffice because it won't support accents (strangely, Kate does). Any suggestions...? Please...?

---

### Post by kuckunniwi on 2015-05-27
```
After this operation, 454 kB disk space will be freed.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en:es:ca:fr:en",
        LC_ALL = (unset),
        LC_TIME = "en_FR.UTF-8",
        LC_MONETARY = "en_FR.UTF-8",
        LC_ADDRESS = "en_FR.UTF-8",
        LC_TELEPHONE = "en_FR.UTF-8",
        LC_NAME = "en_FR.UTF-8",
        LC_MEASUREMENT = "en_FR.UTF-8",
        LC_IDENTIFICATION = "en_FR.UTF-8",
        LC_NUMERIC = "en_FR.UTF-8",
        LC_PAPER = "en_FR.UTF-8",
        LANG = "en_FR.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
```

---

### Post by leunam12 on 2015-05-28
Add the language indicator to your panel and start Libre Office and see if the language is changing for that particular program. Changing it back it's easy, just click on the icon on the panel and select Spanish.

---

### Post by kuckunniwi on 2015-05-28
Nope, didn't work, but thanks for your answer. I looked up the above error I was getting and tried everything I could find on fixing locale issues. Problem seems to be solved, although I'm not sure which command did the trick:

```
sudo locale-gen en_GB en_GB.UTF-8
sudo dpkg-reconfigure locales
```

```
sudo sh -c "echo -e 'LANG=en_GB.UTF-8\nLC_ALL=en_GB.UTF-8' > /etc/default/locale"
```


```
sudo update-locale LC_ALL=en_GB.UTF-8 LANG=en_GB.UTF-8
```

In any case, problem solved! Thanks all! :D

---

