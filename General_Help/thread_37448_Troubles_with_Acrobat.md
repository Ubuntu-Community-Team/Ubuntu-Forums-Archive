---
title: "Troubles with Acrobat"
date: 2005-05-27
forum: General Help
---

### Post by j_baer on 2005-05-27
I am having no luck intalling Adobe Acrobat on my machine. I was hoping for version 7 but will accept anything that works.

Does anyone have it working and if so where did you get it?

Thanks ...

---

### Post by cutOff on 2005-05-27
[QUOTE=j_baer]I am having no luck intalling Adobe Acrobat on my machine. I was hoping for version 7 but will accept anything that works.

Does anyone have it working and if so where did you get it?

Thanks ...[/QUOTE]
How did you install Acrobat Reader??

Try to do as says here

[http://ubuntuguide.org/#acroread](http://ubuntuguide.org/#acroread)

---

### Post by j_baer on 2005-05-27
Ok,

I ran the script lines from the User's guide and they ran without error with the exception the second line should be modified to read acroreader-plugin.

It placed a menu item in the games folder and Acrobat does not load from the desktop or from the browser.

Just for fun I will download v7 from Adobe and install from the tar.

Stay tuned ...

---

### Post by j_baer on 2005-05-27
The solution ...

I install gpdf and set the file association to pdf and it works. It's not embedded in the browser but I can live with that.

Cheers ...

---

### Post by jonrkc on 2005-05-29
Funny, I just did apt-get install acroread and it worked right away. I wonder why yours didn't...  Also, if I click on a .pdf file in Firefox, it opens it up right away in acroread.  Hmm.

I prefer acroread to gpdf because it has quite a few more features.  But gpdf does a decent basic job.

---

