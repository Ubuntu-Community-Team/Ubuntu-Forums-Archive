---
title: "Federal tax prep programs- can Ubuntu run any?"
date: 2014-09-20
forum: General Help
---

### Post by ra7411 on 2014-09-20
Federal tax prep programs- can Ubuntu run any?

---

### Post by QIII on 2014-09-20
Depends on the jurisdiction where you live.  I'm going to assume, for the purposes of my answer, that you live in the US -- but remember that this is a world-wide forum and this answer may not fit where you are.

The absolute and definitive answer is ...

Probably not, at least not natively.  Windows .exes don't run natively in Linux.  There are articles all over the web about people trying to find a good Linux alternative and being somewhat underwhelmed by the choices.

If you talk to many people about Linux, their jaws will slacken, their eyes will glaze over initially until a horrible realization occurs to them, they will scowl and then they will lock down all of their computers because they have taken the FUD hook and believe that all Linux users are evil hackers with nefarious intent.

If you are talking about US Federal taxes, I don't know if TaxACT is still available, but it was not all that impressive as I understand.  Tax Law is extremely convoluted in the US and changes so quickly that some open source developers, without an interest in commercial success, may have little incentive to be sure to keep up with all the details.

(In my line of work, developing code to cover the changes that concern us is constant and frantic.  But we get paid well by our clients to do it.)

There are pretty much three *practical* and *pragmatic* approaches (read: "perhaps anathema to some militant FLOSS types"), some of which may not be very satisfactory for you:

1.  See if you can get TurboTax or something like it to work with Wine.  You'll have to check out the database at winehq.com to see what the rating is on each of them.

2.  Use a virtualization solution like VirtualBox to run Windows and use your favorite Windows tax return software.  Some people find virtualization intimidating (it's not) and you have to have a licensed copy of Windows and *NOT VIOLATE the EULA* -- which means if you have a single-machine license you can't have it installed both in a virtual machine and a real one.  Each is an installation with regard to Microsoft's EULA.  An OEM disk won't do you much good because when it is activated it is locked to the original hardware and the Eye of Sauron will be on you if you try to activate it in a virtual machine.

3.  Use Chrome or Firefox with a User Agent Switcher to make TurboTax's website (for instance) think you are using Windows and do it with their online software.

To be quite frank with you, it is more likely that a commercial interest would be more up to date and detailed in their tax preparation applications.  Just the way it is.

Cheers!

---

### Post by ra7411 on 2014-09-20
I was refering to US federal tax prep programs.
Thanks

---

### Post by fyfe54 on 2014-09-20
I use Turbotax in a Win7 virtual machine and it works just fine.  But every year I look for a native Linux solution.  So far, without success.

Maybe I'll try online this time.

---

### Post by rbmorse on 2014-09-20
TurboTax in a Windows virtual machine is the only usable solution I've found to date, but each new tax season finds me hopefully watching for a Linux-based alternative.

---

### Post by tgalati4 on 2014-09-21
Firefox or google-chrome in linux can fill out any [IRS fillable, PDF tax form]("https://www.freefilefillableforms.com/#/fd") that I have been able to throw at it.  Follow the link and instructions on the IRS website for free, fillable tax forms.  They contract out a 3rd-party company to maintain the PDF files and then electronically submit them for free.  You get a kick-back if there is an error or a confirmation email if the forms were accepted by the IRS.  It's a nice service and not any more difficult than using tax software.  You need to register an account--they use 2-factor authentication that includes knowing your Adjusted Gross Income from a previous tax year.  Once you are registered, any forms submitted are considered digitally signed.

Most of the math is done for you inside the forms (like a spreadsheet).  Values from other forms automatically show up in the correct places.  You can use place-holder values to estimate your taxes.  The placeholders get replaced when you fill out the corresponding form.  Once you have completed your return, you can download the resulting PDF's and either print them for your records, or just keep electronic copies.

The packaged, Windows software walks you through the tax preparation process, but so does the fillable forms website.  So I see little difference between the two, except you cannot use the website as a paid, tax preparer.  It would be nice for a true, linux-supported, tax preparation package, but in the meantime, this works.

Filing taxes is not fun, but at least I don't have to dual-boot.  Now if I could figure a way to pay my taxes with Coffee Beans.

---

### Post by Dennis N on 2014-09-21
The online versions of TurboTax or TaxAct will work with no problems in Ubuntu.

---

