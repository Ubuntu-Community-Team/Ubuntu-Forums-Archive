---
title: "Mounting a .mdf file"
date: 2005-10-28
forum: General Help
---

### Post by zorkerz on 2005-10-28
I just downloaded a .mdf file that should be the image of a cd or dvd. Is there any way to mount these in ubuntu or convert them to .iso.

---

### Post by toorima on 2005-10-28
don''t think you can mount a .mdf so convert with mdf2iso
[http://freshmeat.net/projects/mdf2iso/](http://freshmeat.net/projects/mdf2iso/)

edit: just apt-get install mdf2iso

---

### Post by shadow on 2005-10-28
I've not found a decent solution to this either and find myself booting into windows and firing up alcohol.

mdf2iso would be perfect, if it supported large files.

---

### Post by zorkerz on 2005-10-28
ya thats what ive been doing also useing daemon tools or alcohol 120
anyone know if there is a program that will convert large .mdf files to iso

---

### Post by prototype-f on 2005-12-09
i was also having this problem, after some research and sheer luck i found that i could mount the .mdf images i made in alcohol 120% by using the simple command:

```
mount *image_name.mdf* /directory/name -o loop
```

/directory/name can be anywhere you wish to mount the image to (eg /media/mdf or /mnt/image or whatever), that pretty much works on all of my .mdf files. if you still want to convert them to .iso you could probably use the dd command.

---

### Post by ghostcom97 on 2006-01-10
if you can mount the image then you can burn it with
> growisofs -Z /dev/dvd=/path/to/image.mdf

---

### Post by depele on 2006-07-31
ioctl: LOOP_CLR_FD: Device or resource busy
mount: you must specify the filesystem type


I get this message, and I don't get it fixed to mount it.:x

---

### Post by ricesteam on 2006-08-01
I am too having the same problem...

Please help us noobs out.  I don't understand why I can't mount nor why I am getting these "cryptic" error messages.

---

### Post by auscult on 2007-02-10
Hey I'm bumping this cause I am having the same problem.  It keeps asking for the file system type.... any idea guys?

---

### Post by Vadi on 2008-03-18
> **prototype-f said:**
> i was also having this problem, after some research and sheer luck i found that i could mount the .mdf images i made in alcohol 120% by using the simple command:

```
mount *image_name.mdf* /directory/name -o loop
```

/directory/name can be anywhere you wish to mount the image to (eg /media/mdf or /mnt/image or whatever), that pretty much works on all of my .mdf files. if you still want to convert them to .iso you could probably use the dd command.

Thanks, that worked for me. Just needed sudo in front.

---

### Post by Kerry_W on 2008-03-18
AcetoneISO2 says it will mount mdf files

---

### Post by Vadi on 2008-03-18
Yeah but they don't have a version for 64bit, only 32.

---

### Post by bulletxt on 2008-03-18
you just have to download the sources, follow the README and it will of course work on 64 bit os! very simple! just read the README in the source package from 

[http://www.acetoneiso.netsons.org/viewpage.php?page_id=2](http://www.acetoneiso.netsons.org/viewpage.php?page_id=2)

---

### Post by Vadi on 2008-03-18
Yeah, *just* that. If the devs don't care for a 64 build, and I don't really need one since 1 command did it, I ah will skip that :)

---

### Post by OzzyFrank on 2008-07-07
Downloading my first ever **.mdf** image at the moment, so thanks all for the info on **[COLOR="DarkRed"]mdf2iso[/COLOR]**, though the talk about "large files" is sort of worrying (is there a size limit with **mdf2iso**?). But hey, apparently if that won't work for me I can always use **[COLOR="Purple"]AcetoneISO2[/COLOR]**, which I have running fine on my 64-bit Ubuntu Hardy.

And if anyone is interested in my opinion on whether it is worth the small hassle of installing [COLOR="#800080"]**AcetoneISO2**[/COLOR], I'd say **definitely**! I've used it since version 1, and even got a feature put in at my request (the ability to specify a disc label when creating an .iso from a folder). It is a small and fast little app great for mounting/creating/converting .iso images, and even has features like converting from Mac discs etc. Seems it has yet another feature I didn't know about (though I had never even heard of .mdf files till I went to download the image I am currently getting).

What I would like to know is why are people creating images in fairly unsupported formats like .uif and .mdf, when they could be saving us the hassle of looking for convertors by just creating them as .isos?

---

### Post by OzzyFrank on 2008-07-19
OK, the **Dethklok** album I downloaded I couldn't seem to convert in Ubuntu. I didn't try mounting it anywhere, including **AcetoneISO2**, as I just wanted to see if I could convert the **.mdf** to **.iso** format. Using both **[COLOR="Red"]mdf2iso[/COLOR]** and the newer, more advanced **[COLOR="DarkOrchid"]iat[/COLOR]** (by the same author), I got errors. Basically, despite its name, [COLOR="Red"]**mdf2iso**[/COLOR] was useless as it told me the .mdf wasn't actually the correct format. Then [COLOR="DarkOrchid"]**iat**[/COLOR] set about converting it, got quite a few minutes in, but ended up failing, saying it either wasn't a real image (though the data it gave while trying to convert it said otherwise) or that the image was in fact broken (which, of course, was possible, but I have since ruled that out).

Now, the person who put the image up for download stated that basically any basic burning program (in Windows) should be able to handle it, which isn't the case at all. So I assume he didn't even know what an .iso is, and created the image with **Alcohol 120%**, as the default format for images is .mdf. The one program in Windows that I had installed already and could handle the .mdf images was **[COLOR="Blue"]PowerISO[/COLOR]**, which lets you unpack or burn to disc (and I assume convert to .iso - I didn't even bother to look, as the Burn function was what I needed, and there was a toolbar button for it).

So Ubuntu users should install both [COLOR="Red"]**mdf2iso**[/COLOR] and **[COLOR="DarkOrchid"]iat[/COLOR]** and give them a try first, as I assume they can in fact handle .mdf images, but something in the 2 Dethklok images (album and bonus disc) stumped them both - perhaps because the images were made in **Alcohol 120%**.

Using both in the terminal is pretty straight forward: open a terminal in the folder with the image(s), specify the command, the source file, and destination file (you can leave that out if wanting to keep the orginal prefix). Eg:

**[COLOR="Red"]mdf2iso Dethklok.mdf[/COLOR]** (or **mdf2iso Dethklok.mdf Dethklok-Disc-1.iso**)

**[COLOR="DarkOrchid"]iat Dethklok.mdf[/COLOR]** (or **iat Dethklok.mdf Dethklok-Disc-1.iso**)

Hope all this info helps someone!

---

