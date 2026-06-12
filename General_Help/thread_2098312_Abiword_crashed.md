---
title: "Abiword crashed"
date: 2012-12-26
forum: General Help
---

### Post by anon_private on 2012-12-26
Hi,

I an having trouble with abiiword (2.9.2) in Lubuntu 12.04

On pasting into a document abiword crashed and now the file and a previous version will not open. I get the following messages for the original and saved documents:

AbiWord cannot open file:///media/OS/Users/Andrew/Jobs/To%20Be%20Submitted/NUH_1/PS%20Change%20Officer%20band%205%20-%20September2011.abw. It appears to be an invalid document.

AbiWord cannot open file:///media/OS/Users/Andrew/Jobs/To%20Be%20Submitted/NUH_1/PS%20Change%20Officer%20band%205%20-%20September2011.abw.saved. It appears to be an invalid document.

Is there anotherlight word processor that I can use?

Thanks

---

### Post by Yougo on 2012-12-26
i'm afraid your files have become corrupted. at any rate, you saved them as .abw, which is abiword native format. i dont know any other program that handles that format :( 

you could try to open the file in Gedit or similar simple text editor to see if you can copy the text out of it, in case you wrote a lot that needs to be saved.

------------

if you look in Software Center, and search for "word processor" you get a list of programs. some are extremely lightweight, like Focuswriter, and only meant for producing raw text with as little distraction as possible. 
others like Calligra Words and Libreffice Writer (which you can install without the rest of libreoffice programs like impress or draw, to save space) are used for more graphic work. 
i have no experience with Calligra, but Libreoffice Writer has a wide support of different formats. -just no .abw, sadly

---

### Post by hawthornso23 on 2012-12-26
There is a problem with Abiword in 12.04. A development version of abiword was mistakenly included in 12.04 instead of the stable version. This isn't the kind of program you want to use on files you actually care about as it is unstable and full of bugs. Bug reports have been filed about the use of the wrong version  and I understand there is an attempt being made to get the version rolled back to the stable one. Because 12.04 is LTS however it isn't easy to get the version changed.

My advice is to not use Abiword at all until the problem is fixed. Swich to libreoffice. If you MUST have abiword you should investigate manually installing the stable version.

---

### Post by kansasnoob on 2012-12-26
They shipped a totally borked version of abiword in 12.04:

[http://ubuntuforums.org/showthread.php?t=2004848](http://ubuntuforums.org/showthread.php?t=2004848)

It's much better in 12.10 but if you wish to keep using 12.04 you can use the packages from this PPA:

[https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise)

Just run:

```
sudo add-apt-repository ppa:mrpouit/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install abiword
```

Note: there is also an update in there that effects xfce4 pulse audio but it won't break anything ;)

---

### Post by Yougo on 2012-12-26
^or there's that :)

upgrade, and see of the newer abiword can recover the files. in any case it has less chance of hapening again.

---

### Post by anon_private on 2012-12-26
> **kansasnoob said:**
> They shipped a totally borked version of abiword in 12.04:

[http://ubuntuforums.org/showthread.php?t=2004848](http://ubuntuforums.org/showthread.php?t=2004848)

It's much better in 12.10 but if you wish to keep using 12.04 you can use the packages from this PPA:

[https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise)

Just run:

```
sudo add-apt-repository ppa:mrpouit/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install abiword
```

Note: there is also an update in there that effects xfce4 pulse audio but it won't break anything ;)

Thanks for responding.

I can't see a previous version of abiword in the link!

---

### Post by anon_private on 2012-12-26
> **Yougo said:**
> i'm afraid your files have become corrupted. at any rate, you saved them as .abw, which is abiword native format. i dont know any other program that handles that format :( 

you could try to open the file in Gedit or similar simple text editor to see if you can copy the text out of it, in case you wrote a lot that needs to be saved.

------------

if you look in Software Center, and search for "word processor" you get a list of programs. some are extremely lightweight, like Focuswriter, and only meant for producing raw text with as little distraction as possible. 
others like Calligra Words and Libreffice Writer (which you can install without the rest of libreoffice programs like impress or draw, to save space) are used for more graphic work. 
i have no experience with Calligra, but Libreoffice Writer has a wide support of different formats. -just no .abw, sadly

Thanks for responding.

Is LibreOffice Writer light on memory resources. I have 512MB of RAM

I will need to use .doc formats

---

### Post by Yougo on 2012-12-26
I'm not sure how well libreoffice behaves with that amount of RAM. One way to find out is to try.
To install just Writer, use the following command: ```
sudo apt-get install libreoffice-writer
```
If you decide it's not for you, use this command:

```
sudo apt-get purge libreoffice-*
```

Libreoffice Writer has full (though sometimes a bit quirky, if you use some exotic features) support for .doc files. I haven't had any major problems yet.
It has a bit shaky but improving support for .docx
It's native format is the open standard of .odt, which can also be read by newer versions of ms office.

---

### Post by anon_private on 2012-12-26
> **Yougo said:**
> I'm not sure how well libreoffice behaves with that amount of RAM. One way to find out is to try.
To install just Writer, use the following command: ```
sudo apt-get install libreoffice-writer
```
If you decide it's not for you, use this command:

```
sudo apt-get purge libreoffice-*
```

Libreoffice Writer has full (though sometimes a bit quirky, if you use some exotic features) support for .doc files. I haven't had any major problems yet.
It has a bit shaky but improving support for .docx
It's native format is the open standard of .odt, which can also be read by newer versions of ms office.

Thank you.

Will LibreOffice have any effect on abiword that I have installed?

---

### Post by kurt18947 on 2012-12-27
> **anon_private said:**
> Thanks for responding.

Is LibreOffice Writer light on memory resources. I have 512MB of RAM

I will need to use .doc formats

LibreOffice writer should run on 512 MB. RAM, I've installed LO-writer in Lubuntu on a 512 MB. PIII machine.   I removed Abiword and installed LO-writer only, not the full office suite.  It seems okay but I've only done light usage.  IME LO-writer opens docx files pretty well.  Others with more experience say that saving docx files in LO-writer then opening in MS Office is  unreliable, especially with heavy graphics or formatting.

---

### Post by anon_private on 2012-12-27
> **kurt18947 said:**
> LibreOffice writer should run on 512 MB. RAM, I've installed LO-writer in Lubuntu on a 512 MB. PIII machine.   I removed Abiword and installed LO-writer only, not the full office suite.  It seems okay but I've only done light usage.  IME LO-writer opens docx files pretty well.  Others with more experience say that saving docx files in LO-writer then opening in MS Office is  unreliable, especially with heavy graphics or formatting.


Thanks for responding.

I was asking because I found that the word processor in OpenOffice runs very slowly with 512MB of memory. I noted that LibreOffice writer seems quite a large file and I thought that it might be heavy on resources.

Best wishes for the new year.

A

---

### Post by Yougo on 2012-12-27
have you tried upgrading Abiword yet? seems it's the best option for you and your pc in terms of footprint and compatibility

---

### Post by anon_private on 2012-12-27
I tried upgrading abiword some time ago, but I have a later development version of the program. When I tried to upgrade from abiword but I got the following message:

'Your version is newer than the latest stable version of AbiWord, which is v2.8.6. Most likely you are using a development version.'

I am using ver. 2.9.2

---

