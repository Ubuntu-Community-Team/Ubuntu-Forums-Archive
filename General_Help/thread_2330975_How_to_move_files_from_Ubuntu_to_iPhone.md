---
title: "How to move files from Ubuntu to iPhone"
date: 2016-07-16
forum: General Help
---

### Post by dabech on 2016-07-16
Hi all,

I am new to Linux and would like to know how to move files from  Ubuntu to my iPhone, more specifically mp3 music files. My Ubuntu  version is 16.04 and my iOS version is 9.3.2. When I connect my iPhone  to my PC, it is natively recognized by Ubuntu but I only see my iPhone's  photo folder ("DCIM"), like it does under MS Windows.

  I know this question has been asked multiple times and I've done a  lot of research but I still can't figure it out. I seem to find 2 types  of answers out there: some argue it's just impossible as Apple has  locked down the capability, some others argue that it's possible using  the libimobiledevice library.

  [http://www.libimobiledevice.org](http://www.libimobiledevice.org) claims that it supports all iOS versions until iOS 10 and that it can be used to transfer music.
  This website also mentions the libimobiledevice are in the Ubuntu  "offical repositories". I am not quite sure what it means; but when I  search for libimobiledevice in Ubuntu Software, it does not return any  result.

  I also found this tutorial that looked promising: [http://www.dedoimedo.com/computers/linux-iphone-6.html](http://www.dedoimedo.com/computers/linux-iphone-6.html)
  But running the first set of instructions returned errors:

```
  sudo apt-get install ideviceinstaller python-imobiledevice libimobiledevice-utils libimobiledevice4 libplist2 python-plist ifuse 

E: Unable to locate package libimobiledevice4
E: Unable to locate package libplist2
```

Because I am new to Linux, I am very unfamiliar with the concepts of  installing applications or compiling source code by writing commands in  the terminal, as opposed to just using a nice GUI (e.g. Ubuntu  Software).

  Step by step instructions would be much appreciated. I am usually  pretty good at tech stuff (including programming) but feel completely  lost now.

  Thanks in advance for helping me out.

---

### Post by GU4$+7rxH#@ on 2016-07-16
Hello

Check this page

[U][I][B][http://askubuntu.com/questions/378558/unable-to-locate-package-while-trying-to-install-packages-by-apt](http://askubuntu.com/questions/378558/unable-to-locate-package-while-trying-to-install-packages-by-apt)


[/B][/I][/U]

---

### Post by dabech on 2016-07-17
Thank you so much.
Thanks to your link and the website [packages.ubuntu.com]("http://packages.ubuntu.com/"), I was able to determine that libimobiledevice4 had to be replaced by libimobiledevice6 and libplist2 replaced by libplist3.

The rest of the tutorial that I referenced in my first message then worked pretty well although I struggled using ifuse and figuring out if I was supposed to use it as root (sudo) or user.
After the iPhone has been paired using ```
idevicepair pair
```, here is how I mounted it:

```
sudo mkdir /media/iPhone
sudo chmod 777 /media/iPhone
ifuse /media/iPhone/

```

And that's all. After that I can properly see all the documents (music, etc) in my iPhone.

---

