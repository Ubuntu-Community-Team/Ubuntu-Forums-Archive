---
title: "Is this Deb file for *buntu, Debian, Mint? Or all of them?"
date: 2015-05-28
forum: General Help
---

### Post by triciasurfer on 2015-05-28
I am looking into acquiring a document scanner. In particular, the Brother ADS-2000. On the company's website, Linux users are provided with [two options for this particular scanner]("http://support.brother.com/g/b/downloadtop.aspx?c=us&lang=en&prod=ads2000_us"):
1. rpm
2. deb

I suppose that the Deb file is the better option. But the company website doesn't say if the deb file is designed for Debian, Ubuntu, Mint or some other debian-based Linux distro. Can someone examine [the 64-bit deb file]("http://download.brother.com/welcome/dlf006645/brscan4-0.4.3-1.amd64.deb") ([HTML page which links to the deb]("http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=ads2000_us&os=128&dlid=dlf006645_000&flang=4&type3=566")) and confirm which distros Brother designed it for? 

Thank you for helping a beginner!:p):P

---

### Post by Dennis N on 2015-05-28
Ubuntu uses .deb files to install software, so that would be the correct choice. You can't use the rpm.

---

### Post by triciasurfer on 2015-05-28
Hi, Dennis. Thanks for your reply. So I gather from your reply that if a file is a deb file it will work for any and all debian-based distros (e.g. Ubuntu, Mint, Debian)? Is this correct?

---

### Post by Dennis N on 2015-05-28
It's for any Linux distro that requires .deb files. When you get it downloaded, right-click on it and there is an option to "Open with Ubuntu Software Center". That can be used to install it, but I always use another installer called gdebi, which is in the repositories. When gdebi is installed, you get another option "Open with Gdebi Package Installer". You can install gdebi from the Ubuntu Software Center (search for 'gdebi'), or with Synaptic, or with command line apt-get if you are familiar with that.

---

### Post by Dennis N on 2015-05-28
Your link

[http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=ads2000_us&os=128&dlid=dlf006645_000&flang=4&type3=566](http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=ads2000_us&os=128&dlid=dlf006645_000&flang=4&type3=566)

does mention pre-required procedures for Ubuntu or Debian, so they have Ubuntu in mind. Looks like you are good to go.

---

### Post by triciasurfer on 2015-05-28
thanks, dennis!

---

### Post by Bucky Ball on 2015-05-29
Brother is very Ubuntu/Linux friendly. Use the .deb file and all should be fine.

Go for one of [these]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=ads2000_us&os=128"), depending on 64 or 32bit architecture.

---

### Post by triciasurfer on 2015-05-29
Bucky Ball, thanks for your reply. Yes, I heard that Brother is Linux friendly. :)

I'm private-messaging someone on this UbuntuForums, who told me that they didn't install the Brother deb, and that the deb isn't necessary. But without the deb, how do I scan?

---

### Post by monkeybrain20122 on 2015-05-30
> **triciasurfer said:**
> Bucky Ball, thanks for your reply. Yes, I heard that Brother is Linux friendly. :)

I'm private-messaging someone on this UbuntuForums, who told me that they didn't install the Brother deb, and that the deb isn't necessary. But without the deb, how do I scan?

Just plug it in.

---

### Post by mattharris4 on 2015-05-30
> **triciasurfer said:**
> Bucky Ball, thanks for your reply. Yes, I heard that Brother is Linux friendly. :)

I'm private-messaging someone on this UbuntuForums, who told me that they didn't install the Brother deb, and that the deb isn't necessary. But without the deb, how do I scan?

I have two Canon printers but in my case after I set up the computer to print I was able to scan with Simple Scan without any other issues.  Setting up a printer in my case was relatively simple:  Connect the printer to your computer's USB port, wait a minute, then go to your menu icon (in Lubuntu it is in the lower left corner of your screen, in Xubuntu it is in the top left corner of your screen, in Ubuntu you would click the search icon (IIRC) at the top of your Unity bar (the one with all of the different icons) at the left of your screen), select/search for System Tools, then select Printers.  Next, select Add.  Then select the correct printer.  The press Forward and follow the prompts, be sure to print a test page at the end.  Not all printers are compatible with a Buntu OS but many are and others are saying a Brother printer should work -- I really can't speak knowledgeably beyond that (for example I didn't have any issue with my two Canon printers but there was another thread a while back where someone could not get a different Canon to work).  Canon themselves does not claim their printers work in Linux at all so I count myself fortunate that mine worked so easily.

---

