---
title: "Need help creating desktop launcher for LibreOffice bug workaround"
date: 2021-04-03
forum: General Help
---

### Post by Brent_Santin on 2021-04-03
Hi,

In Lubuntu 20.04 there is a known bug in Libreoffice whereby it produces blank PDFs (instead of what you want it to output to PDF).
There is a work-around. By running LibreOffice Writer from the command line the following way:
> 
[FONT=courier new]SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer[/FONT]

But I'd rather not have to run it from the command line every time I want to use LibreOffice Writer, so I'm trying to figure out how to put this command into a desktop launcher. I just learned how to do desktop launders to start executables and made a few successfully.
However, I am doing something wrong with the syntax in this particular desktop launcher:

> [FONT=courier new][Desktop Entry]
Name=Writer (PDF fix)
Comment=Launcher to start LibreOffice Writer without blank PDF bug
Exec=SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer
Icon=Writer_fixed
Terminal=false
Type=Application
Categories=Office;[/FONT]

Because I get the error message "Invalid desktop entry file: '/home/brent/.local/share/applications/Libreoffice_Writer_fixed_PDF.desktop'

Can anyone see what I'm doing wrong and explain how to implement what I wish to do properly?

Thanks.

---

### Post by norobro on 2021-04-03
I have no idea whether this will work or not but try something like the following:```
Exec=libreoffice -env:SAL_VCL_QT5_USE_CAIRO=true --writer
```From here: [https://help.libreoffice.org/7.0/en-US/text/shared/guide/start_parameters.html#par_id20161204014126760](https://help.libreoffice.org/7.0/en-US/text/shared/guide/start_parameters.html#par_id20161204014126760)

---

### Post by CatKiller on 2021-04-04
In general, you'd use *env*. So something like
```
Exec=env SAL_VCL_QT5_USE_CAIRO=true "libreoffice --writer"
```
in this case. I don't *know* that you'd need the "" but it shouldn't hurt.

---

### Post by Holger_Gehrke on 2021-04-04
> **CatKiller said:**
> In general, you'd use *env*. So something like
```
Exec=env SAL_VCL_QT5_USE_CAIRO=true "libreoffice --writer"
```
in this case. I don't *know* that you'd need the "" but it shouldn't hurt.

Well, actually they **do** hurt. The quotes break the word splitting and env will try to execute a program named 'libreoffice --writer' with the space as part of the name of the executable file's name. Since there is no such file ...

Holger

---

### Post by TheFu on 2021-04-04
libreoffice is just a softlink to the old staroffice startup script.
```
$ file /usr/bin/libreoffice /usr/bin/soffice
/usr/bin/libreoffice: symbolic link to ../lib/libreoffice/program/soffice
/usr/bin/soffice:     symbolic link to ../lib/libreoffice/program/soffice
```


# file /usr/lib/libreoffice/program/soffice
/usr/lib/libreoffice/program/soffice: POSIX shell script, ASCII text executable[/CODE]

So ... if it was me, I'd copy /usr/lib/libreoffice/program/soffice to  /usr/lib/libreoffice/program/soffice.local, changing the name slightly to avoid problems, and add the desired environment variable there.  Leaving it in the same directory is required because the script figures out which directory it is in and assumes other things are there as well. Initially, I tried copying the script to my ~/bin/ and modifying it there. That failed because /usr/lib/libreoffice/program/oosplash wasn't available.  Anyways, basically, add 
```
SAL_VCL_QT5_USE_CAIRO=true
export SAL_VCL_QT5_USE_CAIRO
```
near the top of /usr/lib/libreoffice/program/soffice.local .

Next, make a symlink from ../lib/libreoffice/program/soffice.local to /usr/bin/ (this is needed because the script 
and finally
call it with whatever options the other .desktop file for Writer does.

To run it:
```
$ soffice.local --writer
```

I haven't tested it for PDFs, but *soffice.local --writer* is working and it created a TEST.pdf file correctly. 
Would be interesting to know if it works for others. The version here is : 
```
ii  libreoffice-writer                    1:6.4.6-0ubuntu0.20.04.1
```

The env= .... --writer would be easier, by far, provided that it works. If that isn't working, I'd try to have it run inside a shell first.

---

### Post by Brent_Santin on 2021-04-04
> **norobro said:**
> I have no idea whether this will work or not but try something like the following:```
Exec=libreoffice -env:SAL_VCL_QT5_USE_CAIRO=true --writer
```From here: [https://help.libreoffice.org/7.0/en-US/text/shared/guide/start_parameters.html#par_id20161204014126760](https://help.libreoffice.org/7.0/en-US/text/shared/guide/start_parameters.html#par_id20161204014126760)

That does still lauch Libreoffice Writer, but does not fix the blank PDF issue. So I assume it does not properly pass the arguement SAL_VCL-QT5_USE_CAIRO=true onto libreoffice.

---

### Post by Brent_Santin on 2021-04-04
> **CatKiller said:**
> In general, you'd use *env*. So something like
```
Exec=env SAL_VCL_QT5_USE_CAIRO=true "libreoffice --writer"
```
in this case. I don't *know* that you'd need the "" but it shouldn't hurt.

With the quotation marks present "something" happens (no error message) but Writer never starts.
Without the quotes, Libreoffice starts and prints PDFs properly, so ***THANK YOU VERY MUCH***!

Just for future reference, this is the desktop launcher that works:

```

[Desktop Entry]
Name=Writer (PDF fix)
Comment=Launcher to start LibreOffice Writer without blank PDF bug
Exec=env SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer
Icon=Writer_fixed
Terminal=false
Type=Application
Categories=Office;
```

---

### Post by CatKiller on 2021-04-04
> **Holger_Gehrke said:**
> Well, actually they **do** hurt. The quotes break the word splitting and env will try to execute a program named 'libreoffice --writer' with the space as part of the name of the executable file's name. Since there is no such file ...

Holger

OK, good to know. My thinking was that the --writer part needed to stay with the libreoffice part rather than with the env part.

---

### Post by ActionParsnip on 2021-04-04
Could make a script then have the launcher run the script

---

