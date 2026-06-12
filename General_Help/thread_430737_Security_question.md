---
title: "Security question"
date: 2007-05-02
forum: General Help
---

### Post by ascus4 on 2007-05-02
I hope this is in the proper section.  

I understand that Linux is more secure against malware and viruses than a windows machine.
My understanding is that the security and the need for root access apply to malicious code that tries to install or change something on your harddrive BUT...

What if the code is HTML.  You hear in the news lately about the malicious or corrupt wab sites that hack into your browser.  So...what if the malicious code is HTMl JAVA, Active X or something else that attacks through the browser or a JAVA applet or something, rather than through the operating system.

Did I explain that right?

---

### Post by Tomosaur on 2007-05-02
> **ascus4 said:**
> I hope this is in the proper section.  

I understand that Linux is more secure against malware and viruses than a windows machine.
My understanding is that the security and the need for root access apply to malicious code that tries to install or change something on your harddrive BUT...

What if the code is HTML.  You hear in the news lately about the malicious or corrupt wab sites that hack into your browser.  So...what if the malicious code is HTMl JAVA, Active X or something else that attacks through the browser or a JAVA applet or something, rather than through the operating system.

Did I explain that right?

There few possibilities for things like this to happen. The people who specify HTML code (which is not really code, more of a 'description' of how a page should look), and those who specify JavaScript code, take great care to not allow code which can compromise a person's security / privacy. However - the implementation of the specification is largely browser-dependent, so you should really talk to the people who make the browser. It has very little to do with the operating system.

If you're asking whether a hacker can gain access to your machine **through the browser**, then the short answer is 'no'. The long answer is 'yes, but'. If the browser is badly programmed, then **theoretically**, an attacker could exploit a security hole in the browser and allow execution of arbitrary code. They should not be able to do this through HTML or JavaScript or any other web-language, only through exploiting a bug in the actual browser software (which is again, theoretically possible by using HTML or JavaScript, but only if the browser is very buggy, and recognises bad code, which all browsers should). However, Linux' user priveleges model means that even if an attacker did get access to your machine, the code they run could only do damage to your home directory, which is generally not much of a concern, because it's not critical information (or at least, it shouldn't be). If they wanted to bring down a Linux box, they would have to:

a) Know of a really big security hole in your browser.
b) Know of a really big security hole in Linux.

Your browser should have no big security holes, and Linux has none either, so there's nothing to worry about.

There are a myriad of other 'possible' ways an attacker could get into your system, but you have to remember that they are only **theoretical**. In practice, getting access to any Linux system is incredibly difficult, and any security holes found are normally patched and closed within a matter of days, if not hours.

---

### Post by aysiu on 2007-05-02
NoScript is a might fine extension to have. I have noticed over the years that most of Firefox's exploits are Javascript-related.

---

