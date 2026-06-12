---
title: "PHP links open in Quanta :("
date: 2006-10-21
forum: General Help
---

### Post by Zeroangel on 2006-10-21
Hey all,

I'm a web developer and Kubuntu user, and by default I have local PHP files open in Quanta. However, every time I click on a link in Kopete, Kontact or whatever the file will open in Quanta, when I actually want it to open in Firefox!

Is there any way to adjust the mime-type so that non-local files open with the web browser instead of Quanta?

---

### Post by aysiu on 2006-10-21
No, and this is one of the things I find annoying about KDE/Konqueror.

This is the #1 major reason I don't use Konqueror for web browsing, even when I'm in KDE. My file associations have .php and .html open with Kate, and when I use Konqueror, it tries to open all webpages with Kate instead of within Konqueror.

---

### Post by JacobSteelsmith on 2008-04-16
Well, there is. In case anyone else stumbles onto this old post, here's what you do. Create a file on your desktop of the type you want to change (test.php in this instance).

Using kde (kubuntu), right click on the file and click Open With... Check "Remember application association for this type of file." 

Using gnome (ubuntu), right click on the file and choose properties. Select the open with tab, choose the application, then click ok. 

This works for html files as well. All of the links I would get in email and through IM would open with Kate.

---

### Post by Wim Sturkenboom on 2008-04-16
@JacobSteelsmith

I think you misunderstood the problem. You are referring to the association between a program and a file type.
In the first post that **was** done (PHP files open (are associated) with Quanta).

However, if someone places a link to a php webpage in e.g. an email and the user tries to open that link, it will also open in Quanta and one wants it to open in e.g. Firefox or Konqueror.

I don't use KDE so I can not test and the problem might have been solved with newer versions of Kopete, KDE etc.

---

