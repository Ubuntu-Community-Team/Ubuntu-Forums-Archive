---
title: "Playing commercial DVDs 16.04"
date: 2016-05-05
forum: General Help
---

### Post by HereInOz on 2016-05-05
Hi All,

I am attempting to play a commercial DVD in a computer running 16.04.  

I have installed libdvdcss2, and done the configure, but still no joy.  The thing I find interesting is that, when this computer was running 15.10, without lidvdcss2 installed, it could "mount" the DVD, but was unable to play it, until libdvdcss2 was installed and configured.  Then all was well.

Now, with 16.04, with or without libdvdcss2, the system is unable to even detect that the DVD is there.  

Drive faulty?? I set up another computer, different hardware, different format (laptop rather than desktop) only to find the same thing happens.  

DVD faulty??  Other commercial DVDs fail to be recognised either.  "Home burnt" video DVDs play faultlessly.

I have been doing some searching and I know that others are having similar issues, but I have yet to find a solution. Has anyone else found this and have you been able to sort it out yet?

Hope you can help.

Regards,

Alan

---

### Post by QDR06VV9 on 2016-05-06
> **HereInOz said:**
> Hi All,

I am attempting to play a commercial DVD in a computer running 16.04.  

I have installed libdvdcss2, and done the configure, but still no joy.  The thing I find interesting is that, when this computer was running 15.10, without lidvdcss2 installed, it could "mount" the DVD, but was unable to play it, until libdvdcss2 was installed and configured.  Then all was well.

Now, with 16.04, with or without libdvdcss2, the system is unable to even detect that the DVD is there.  

Drive faulty?? I set up another computer, different hardware, different format (laptop rather than desktop) only to find the same thing happens.  

DVD faulty??  Other commercial DVDs fail to be recognised either.  "Home burnt" video DVDs play faultlessly.

I have been doing some searching and I know that others are having similar issues, but I have yet to find a solution. Has anyone else found this and have you been able to sort it out yet?

Hope you can help.

Regards,

Alan

Do not know why this is a problem for a few but try this:
For 32 and 64 bit versions of "libdvdcss2", direct download below, just install with Gdebi after download:

[http://mirror.home-dn.net/debian-multimedia/pool/main/libd/libdvdcss/](http://mirror.home-dn.net/debian-multimedia/pool/main/libd/libdvdcss/)

---

### Post by kansasnoob on 2016-05-06
What desktop environment are you using? As you say you're not alone:

[http://ubuntuforums.org/showthread.php?t=2323204](http://ubuntuforums.org/showthread.php?t=2323204)

But I've not been able to reproduce the problem.

---

### Post by T.J. on 2016-05-06
> **kansasnoob said:**
> What desktop environment are you using? As you say you're not alone:

[http://ubuntuforums.org/showthread.php?t=2323204](http://ubuntuforums.org/showthread.php?t=2323204)

But I've not been able to reproduce the problem.

Please be aware that - just as a general rule - we probably shouldn't be discussing libdvdcss in the forums.  It has dubious legal status at best, and as far as I know, the forum Terms ban discussions regarding how to install or use things that are illegal.  I can't help you with libdvdcss.

Since the problem you are having is probably not an libdvdcss issue, I feel free to make comment.  I'd bet it is a problem with your environment's auto-mounter.  I'd try making sure the disc is properly mounted before attempting playback.

---

### Post by QDR06VV9 on 2016-05-06
This is in response to the post saying it was illegal to watch DVDs in the USA. I thought I would clarify legal DVD use with free software in the United States.

Section 1201 of the DMCA specifically outlaws the distribution of circumvention tools.

 >    No person shall manufacture, import, offer to the public, provide, or  otherwise traffic in any technology, product, service, device,  component, or part thereof, that is primarily designed or produced for  the purpose of circumventing a technological measure that effectively  controls access to a work protected under this title

-DMCA 1201(a)(2)

It does not outlaw the use of those tools. Fair use of circumvention tools is legal according to the DMCA

     Nothing in this section shall affect rights, remedies, limitations, or  defenses to copyright infringement, including fair use, under this title

-DMCA 1201(c)(1)

So, is it legal for Ubuntu to distribute libdvdcss2 in the US? _**No**_. Is it legal to watch DVDs on Ubuntu using libdvdcss2 in the US? _**Yes.**_ No one inside the US can distribute that program to you,

---

### Post by T.J. on 2016-05-06
[SIZE=2][FONT=arial]> **runrickus said:**
>  Is it legal to watch DVDs on Ubuntu using libdvdcss2 in the US? _**Yes.**_ 

I apologise that this is a bit off-topic, but I feel it is important to discuss the legalities here. I won't discuss anything related to downloading it or its actual use.


First, I admit I am not a lawyer, so my advice is not as good. I am familiar with the law, having worked in a number of libraries. The answer is not "yes" at all. Any software that circumvents DRM is likely to be illegal in the United States.  

[COLOR=#333333]**"(A)**[/COLOR][/FONT][/SIZE][COLOR=#333333][FONT=Verdana][SIZE=2][FONT=arial]No person shall circumvent a technological measure that effectively controls access to a work protected under this title. The prohibition contained in the preceding sentence shall take effect at the end of the 2-year period beginning on the date of the enactment of this chapter." (17 U.S. Code § 1201 - Circumvention of copyright protection systems)

There are exceptions granted by the Head Librarian of the Library of Congress, to be reviewed every few years.  Libdvdcss has never been granted that status, but it has never been tested in a court either.

Second, "fair use" is not a right, it is only a legal defense **after** you have been charged.  You can plead a "fair use" defense successfully, but it is not a guarantee.  If convicted, a U.S. citizen would face a federal felony charge and likely prison. 

Now, that said, I personally believe that it is *unlikely* that they would elect to prosecute any single individual for the using of libdvdcss, because its use is so widespread, but it is* technically* a felony. Whether or not your using it is a crime is for a court to judge. By using it or promoting its use, you are taking a risk.  That is why Canonical, Debian or anyone else does **not** endorse using it (even if they do not distribute it because of the distribution clause).

In my opinion, a person could make a defense that their prosecution is unjust as every other user is not being prosecuted even if they can be easily discovered - for example by downloading VLC for Windows. The only other possible defense that I can imagine is the argument for "interoperability" because the DVD Consortium does not typically license a legal DVD player for Linux.  However, that might be considered specious, especially since Fluendo used to license one a few years ago.   Ripping the DVD would probably entirely deny any "fair use" defense, because you have the ability to purchase a digital copy by other means, but are choosing to create your own - denying the copyright owner deserved income.  Arguing an "interoperability" defense for digitized copies would probably be thrown out because you can watch streams on Linux using Chrome EME. 

In any of the above cases, whether or not you have purchased the DVD is actually irrelevant to your defense.

[/FONT][/SIZE]
[/FONT][/COLOR]

---

### Post by HereInOz on 2016-05-06
I think you are right, TJ.  It is not really a libdvdcss problem.  Rather it is an auto-mount issue.  I shall look along those lines and see what I can find.

Thanks for all your help.

---

### Post by T.J. on 2016-05-06
> **HereInOz said:**
> I think you are right, TJ.  It is not really a libdvdcss problem.  Rather it is an auto-mount issue.  I shall look along those lines and see what I can find.

Thanks for all your help.

You're very welcome.  =)

---

