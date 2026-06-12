---
title: "glib-dev"
date: 2007-09-20
forum: General Help
---

### Post by Charlatat on 2007-09-20
Sorry if this is in the wrong forum, but kind of at my wit's end.

Trying to work with Mono on getting a simple gui working on my Feisty machine. Getting a System.DLLNotFoundException:gdiplus.dll error.

Tried the Mono mailing lists, so they recommending compiling libgdiplus. I'm getting ./configure errors which they deemed is because I'm missing the glib-dev packages. 

But they can't/won't tell me what those packages are or where I can find them.  Can anyone help me out?  Thanks

---

### Post by Maestro23 on 2007-09-20
Use Synaptic or Command to install **libc6 and libc6-dev**.  See if that does the trick.  You can look them up in Synaptic for a description of what they are.

---

### Post by Charlatat on 2007-09-20
Yes, both packages are installed and at the latest version.

---

### Post by Maestro23 on 2007-09-20
You've got build-essential installed also, right?

---

### Post by Wolki on 2007-09-20
glib is not the same as libc. Try installing libglib2.0-dev.

Do you have libgdiplus installed?

[edit] also take a look at [http://www.mono-project.com/DllNotFoundException](http://www.mono-project.com/DllNotFoundException)

---

### Post by Charlatat on 2007-09-20
Yes, libglib2.0-dev and libgdiplus are installed. After installing a LOT of dev packages, I've been able to make ./configure work. Didn't solve my problem, though.

Thanks for the link, think that's exactly what's going on. However, in the documentation it says to add the /usr/local/lib path to the ld.so.conf file. But it doesn't say how exactly to add it (another include statement or what?). 

Can someone lend a hand with that?

Thanks again.

---

### Post by Wolki on 2007-09-20
> **Charlatat said:**
> Thanks for the link, think that's exactly what's going on. However, in the documentation it says to add the /usr/local/lib path to the ld.so.conf file. But it doesn't say how exactly to add it (another include statement or what?). 


I think you just need to add it directly to the file (ie, make a new line and paste it there). The include seems to be for reading from other files.

[edit] bean #1000 o_O

---

### Post by Charlatat on 2007-09-20
yup, just adding another line with "/usr/local/lib" seemed to fix the ldconfig problem. Was able to find libgdiplus.so after that.

However, still get the DLLNotFoundException:gdiplus.dll error when running the app.  

Think I'm gonna abandon WinForms, and see if I can get a GTK app working...

---

