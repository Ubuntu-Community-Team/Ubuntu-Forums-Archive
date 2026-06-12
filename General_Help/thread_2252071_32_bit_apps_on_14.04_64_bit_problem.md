---
title: "32 bit apps on 14.04 64 bit problem"
date: 2014-11-08
forum: General Help
---

### Post by Claude_Sutton on 2014-11-08
Ubuntu 14.04 64 bit.

I have a 32 bit app, Kintraks, which is a dog pedigree program that I must be able to run.

With 12.04, I could run it by installing ia32libs.

I have read a little about multiarch and apparently it would solve my problem, however all  I can learn about it is that it must be used in conjunction with apt-get install.

Since Kintraks is not in a Ubuntu approved repository, it is not possible to use apt-get.

It must be downloaded directly from the Kintrak web site.

So how to get Kintrak to run?  I have hundreds of dogs in the data base and I must be able to run it.

---

### Post by kostkon on 2014-11-08
Do you get any output, specifically errors and warnings, when running it from the terminal? Would you mind pasting it here?

It doesn't matter if the app comes from a 3rd party source, you can still use multiarch, as long as you know what libs it needs to be able to run.

---

### Post by landstander on 2014-11-08
The maker of Kintraks appears to only be providing a proprietary executable file for Linux users along with included libraries for running that file. This means the main program "Kintraks" looks for its supplied libraries in the folder they came in. So you have a Kintraks executable program, and the folder that program is in, has a "Kintraks Libraries" folder which is where the main program looks for its libraries.

I've downloaded the file to my computer to test this out to see if this indeed is the case. The Kintraks program was already labeled as executable right out of the zip file so I clicked on it and there was a message about storing data locally. Click "yes" when you see that window and Kintraks then openes up just fine and appeared to be working ok. However when I shut the program down there was some errors (most likely due to the developer only offering a 32bit program that was run in a 64bit environment).

So in short you might not need to do anything but download and run that program. If it doesn't work then you may need to consider asking the developer if he or she could make a 64bit version. They are asking for your input and bug reports on the Kintraks website right near the download button for the Linux files being offered. So maybe they would be willing to go the extra mile if you let them know there was some interest in their software.

If not then hopefully someone else can offer advice on setting up a virtual 32bit environment or sandbox of some kind to run this program in. You could also try downloading the Windows version of Kintraks to see if it will run in Wine under Linux, but most programs don't work in Wine so hopefully someone else has some better idea's if none of this was helpful.

---

### Post by coldcritter64 on 2014-11-08
This next link may be of help to your running a 32 bit app like you describe OP.  [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
I haven't tried to set up a 32 bit chroot sandbox since Natty (11.04), don't know how easy or even effective this idea will be on later Ubuntu releases. Good luck.

---

### Post by Claude_Sutton on 2014-11-17
I have downloaded the package again and it simply will not run on my sytem.

Before I will do the chroot sandbox thin, I will scrap it.

So not solved but waiting and watching to see if anyone has a reasonable fix.

---

### Post by landstander on 2014-12-28
It would be helpful if you define what you mean by "reasonable fix".

The chroot sandbox option posted by coldcritter64 might be the best option for attempting to run a proprietary program from a developer that does not offer that program in native 64bit architecture. Noting that it is more the developers perogative to make their software useable then it is the general Ubuntu user population's responsability to do so.

---

