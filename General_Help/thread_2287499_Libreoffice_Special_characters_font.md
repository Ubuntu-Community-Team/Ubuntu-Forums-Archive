---
title: "Libreoffice Special characters font"
date: 2015-07-20
forum: General Help
---

### Post by andfree on 2015-07-20
Is there any special character font coming with libreoffice (calc) 4.2.8.2 on Lubuntu 14.04 or I should add one (e.g. webdings)? And, if I should add one, how to do this? Thanks.

---

### Post by sudodus on 2015-07-20
Maybe you can add the Microsoft fonts, that come with the restricted extras.

```
sudo apt-get install lubuntu-restricted-extras
```

Click on TAB and then Enter to accept the EULA for those fonts.

-o-

This package depends on some commonly used packages in the Lubuntu multiverse repository.

Installing this package will pull in support for Microsoft fonts, Flash plugin, DVD playback, LAME (to create compressed audio files) and patent codecs for Chromium.

Please note that this does not install libdvdcss2, and will not let you play encrypted DVDs. For more information, see

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Please also note that packages from multiverse are restricted by copyright or legal issues in some countries. See

[http://www.ubuntu.com/ubuntu/licensing](http://www.ubuntu.com/ubuntu/licensing)

for more information.

---

### Post by vasa1 on 2015-07-20
> **andfree said:**
> Is there any special character font coming with libreoffice (calc) 4.2.8.2 on Lubuntu 14.04 or I should add one (e.g. webdings)? And, if I should add one, how to do this? Thanks.
Is there something specific you need?

LibreOffice Calc offers something called *Dingbats* under Format, Cells, Font.

I've managed to avoid installing *ttf-mscorefonts-installer* :)

---

### Post by andfree on 2015-07-20
Thank both of you. Indeed, Dingbats are available. I was looking for something help me to solve [this problem]("http://ask.libreoffice.org/en/question/53373/search-for-text-part-written-on-specific-font-solved/") but I think there's no a good reason to continue. Thanks again.

---

### Post by vasa1 on 2015-07-20
> **andfree said:**
> Thank both of you. Indeed, Dingbats are available. I was looking for something help me to solve [this problem]("http://ask.libreoffice.org/en/question/53373/search-for-text-part-written-on-specific-font-solved/") but I think there's no a good reason to continue. Thanks again.
Pity you didn't provide the link in the first post itself :)

Interesting to see Ubuntu and Sans fonts described as culprits repeatedly :)

---

### Post by andfree on 2015-07-21
:smile:

It was not a blame, of course! It was just because all this made me feel a little like Hercule Poirot :smile:

Thanks again

---

