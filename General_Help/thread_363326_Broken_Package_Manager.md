---
title: "Broken Package Manager"
date: 2007-02-16
forum: General Help
---

### Post by kiwidipstick on 2007-02-16
Hi, I downloaded virtualbox for edgy and installed. Something went wrong and I get the following message;an error occurred, *please run package manager from the right click menu or apt-get in a terminal to see what is wrong*.*The error message is ;' unknown error' exceptions. System error (E:The package virtualbox needs to be reinstalled but I can't find the archive for it"*
I was directed to the wiki on how to install and it read it through. Under trouble shooting, my problem seems to be listed, saying to open package manager and search for virtualbox and then right click on it in the right hand pane and choose uninstall. However my search shows virtualbox but only in the left hand pane and you do not have an option to right click on it.
Sorry for the lengthy story. Can anyone assist please as I cannot use package manager any more.
Cheers.:)

---

### Post by roland on 2007-02-17
> **kiwidipstick said:**
> Hi, I downloaded virtualbox for edgy and installed. Something went wrong and I get the following message;an error occurred, *please run package manager from the right click menu or apt-get in a terminal to see what is wrong*.*The error message is ;' unknown error' exceptions. System error (E:The package virtualbox needs to be reinstalled but I can't find the archive for it"*
I was directed to the wiki on how to install and it read it through. Under trouble shooting, my problem seems to be listed, saying to open package manager and search for virtualbox and then right click on it in the right hand pane and choose uninstall. However my search shows virtualbox but only in the left hand pane and you do not have an option to right click on it.
Sorry for the lengthy story. Can anyone assist please as I cannot use package manager any more.
Cheers.:)

You said that synaptic only displays virtualbox in the left-hand column, that means there is no package called virtualbox. So, did you try to install the package with Synaptic, or directly from a downloaded .deb-package? What you could try to solve this problem is using apt-get from the terminal. Try ```
sudo apt-get check
``` first, without any instances of Synaptic open. If this gives no error messages, the next step is ```
sudo apt-get clean
```. This should get rid of any incorrectly downloaded packages. Then, as a last step, try ```
sudo apt-get remove --purge virtualbox
```. Now the package should be removed completely. I actually presume that this sequence of commands will not go without errors, could you please post the error messages, if any?

To correctly install the package, without it being in the standard Ubuntu package repository, you have to download it yourself. To make sure you have the most up-to-date package repo, run ```
sudo apt-get update
``` on a terminal. Then, start synaptic and do the search for virtualbox again. If there is no virtualbox, it is not in the repository. As soon as you have the .deb-package, you can run ```
sudo dpkg -i virtualbox.deb
``` on a terminal, where virtualbox.deb should be the correct filename.

Please post the results here, I like feedback. Good luck!

---

### Post by kiwidipstick on 2007-02-17
Hi Roland, I installed virtual box from a download (the ubuntu edgy version) and tried to install with the GDebi package installer.
As per your suggestions, I have done sudo apt-get check and the response is: [I]E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
[/I]
Thanks for your assistance Roland, I await your reply, James.

---

### Post by roland on 2007-02-17
Dear James,

I'm afraid I'm going to stick to the command-line ;) From the dpkg-manpage (man dpkg): "A package marked reinst-required is broken and requires reinstallation. These packages cannot be removed, unless forced with option --force-reinstreq." So, the solution should be: ```
sudo dpkg --purge --force-reinstreq virtualbox
```
If this succeeds, you can reinstall the package with ```
sudo dpkg -i virtualbox.deb
```

---

### Post by kiwidipstick on 2007-02-17
Roland, your first suggestion gives me the response; command not found. James.:-?

---

### Post by roland on 2007-02-17
Ah, yes.. I wrote "dkpg", I meant "dpkg". Does that work?

---

### Post by kiwidipstick on 2007-02-17
Alas, no go either! Sure do appreciate your time and patience. James.

---

### Post by kiwidipstick on 2007-02-18
Aha, tried again and this time I get this response;
 dpkg: unknown force/refuse option `reinstreq'
Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
Does this help at all. James.

---

### Post by quicktime1 on 2007-02-23
Im in a similar situation, 

"E: could not get lock /var/lib/dpkg/lock - open (11 resource temporarily unavailable)"
"E: unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

...is what I get after sudo apt-get check.

And this is the message Package Manager gives me when I tried to click on it.

"E: the package virtualbox needs to be reinstalled but I cannot find an archive for it"

Thank you!

---

### Post by bob-aptllc on 2007-02-23
After I downloaded the VirtualBox .deb package to my desktop, I tried to install by right-clicking. The first result was a dependency error, but then the same error message you are receiving that VirtualBox needs to be reinstalled but Synaptic was not able to find an archive. (The full saga is at [http://ubuntuforums.org/showthread.php?t=367515](http://ubuntuforums.org/showthread.php?t=367515).) Synaptic was broken and not able to locate any package. I was not able to delete the VirtualBox (0 byte) faulty installation using Aptitude on the terminal.

I concluded that a fresh install of Edgy was the quickest and surest fix. I then followed the instructions for installing VirtualBox from the helpful folks at ubuntugeek.com: [http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html). VirtualBox then installed properly. :) 

-Bob

---

