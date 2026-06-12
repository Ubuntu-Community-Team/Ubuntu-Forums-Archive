---
title: "Installing fonts for scholars"
date: 2006-11-14
forum: General Help
---

### Post by finferflu on 2006-11-14
Hi all,
I'm a Biblical Studies student, so it is vital for me to have certain fonts installed, such as Greek and Hebrew fonts.

I've just found this website: [http://scholarsfonts.net/cardofnt.html](http://scholarsfonts.net/cardofnt.html)
It says people have succeeded in installing those fonts on Mandrake 10.1, but it doesn't explain how to install fonts neither on Mandrake nor on any linux system. I've downloaded the package and all that is inside is a User's Manual, an installation guide (for Windows and Mac), and a file called Cardo98s.ttf, which I know is the only thing I'm interested in right now.

I'm very confused about fonts, and I've never managed to install them without aptitude.. is there anyone who can help me please?

Thanks for your time!

---

### Post by matthew on 2006-11-14
One easy way to install fonts is to copy the .ttf file into a hidden folder in your /home directory called /.fonts

In the file browser this is quite easy. Open your /home directory. To to View->Show Hidden Files. Then copy the .ttf file from wherever it is to the .fonts folder. This will work for any valid ttf file.

Let me go test it now with the file you mention...

EDIT: that method worked fine for me. I can see and use the new font in OpenOffice. I didn't try the Hebrew, etc., but in English anyway it works well.

---

### Post by finferflu on 2006-11-14
Thanks for that!
I didn't have any .fonts folder in my home directory, so I just created one, and copied the file in there.

It worked! Thank you!

---

### Post by bdwetzel on 2006-12-06
Hi, I need to add some new fonts.  So, I did like you said but when I showed the hidden files in my home folder there was not a .fonts folder.  Could it be somewhere else?

---

### Post by finferflu on 2006-12-06
As I said above, there was no .fonts folder, so I had to create one.

Type in the terminal:

```
cd ~
mkdir .fonts
```

And you'll have your .fonts folder ready ;)

---

