---
title: "Albumart Cover Downloader"
date: 2007-06-03
forum: General Help
---

### Post by Kingfield on 2007-06-03
You know this program? The one run with the command albumart-qt? Well, i recently did a clean install of feisty, and now the homepage has disappeared, i was wondering if anybody has it? Thanks to anyone who could help.

---

### Post by Kingfield on 2007-06-03
Bump

---

### Post by Kingfield on 2007-06-03
~~~~~~~~~~~~~~~~~~~~~~bump

---

### Post by Kingfield on 2007-06-04
Bump Somebody Please Reply

---

### Post by Titus A Duxass on 2007-06-04
I have it on a machine, but that machine is 5000km away.
I think I have it on my laptop, when the battery refresh utility has done its thing I will look.

I think the website was removed for legal reason, I know amazon were not too happy with that package.

The altenative is to manually download the images.

---

### Post by Kingfield on 2007-06-04
Oh... i was wondering why it disappeared without a trace, thanks a lot if you can manage to find it!:D

---

### Post by Kingfield on 2007-06-04
hmm anyone else could help me out please?

---

### Post by Titus A Duxass on 2007-06-05
Sorry, can't find a copy.

---

### Post by Kingfield on 2007-06-05
awww... ****... anyone else? pleasesssssss

---

### Post by Titus A Duxass on 2007-06-05
A little bit of Googling resulted in this:

[http://directory.fsf.org/albumart.html](http://directory.fsf.org/albumart.html)

---

### Post by Kingfield on 2007-06-05
> **Titus A Duxass said:**
> A little bit of Googling resulted in this:

[http://directory.fsf.org/albumart.html](http://directory.fsf.org/albumart.html)

lolz, i have checked through the first what, 15 pages of google? i tried that, it gets some error and i cant open it,.

---

### Post by Kingfield on 2007-06-06
Bump Plz

---

### Post by Kingfield on 2007-06-07
Bumppppp!!!!!!

---

### Post by Kingfield on 2007-06-08
Bump Wtf

---

### Post by mglukhovsky on 2007-06-09
I finally figured out how to get a copy of Album Cover Art Downloader. I did a bit of googling, and found a copy of the *.tar.gz on the Gentoo mirrors. Any one of them will work, but here's the one I used: [http://ftp.roedu.net/mirrors/gentoo.org/distfiles/]("http://ftp.roedu.net/mirrors/gentoo.org/distfiles/"). Look for the file "albumart-1.6.0.tar.gz".

If you want to build the file from source into a *.deb for squeaky clean package management:

1) Install (from Synaptic or command line using apt-get) the packages build-essential, fakeroot, debhelper, and pyqt-tools.
2) Extract albumart-1.6.0.tar.gz to the folder of your choice.
3) Open a terminal, then cd to the folder to which you extracted albumart-1.6.0.tar.gz.
4) Build your *.deb by issuing the following command:
```
fakeroot debian/rules binary
```
5) The resulting built package, albumart_1.6.0-1_all.deb, should appear in the parent folder.
6) You can now install the *.deb by either using GDebi or the command line (dpkg -i albumart_1.6.0-1_all.deb).

There is one bug with the package that needs to be fixed before you can use Album Cover Art Downloader in Feisty.

1) Open a terminal, and navigate to the folder that contains the files for the application:
```
cd /usr/lib/albumart/
```
2) Open the offending file in gedit as root:
```
sudo gedit albumart_images.py
```
3) Insert the following as the first line of the file:
```
#coding:utf-8
```
4) Save the file, then exit gedit.


To run the program, either issue the following from a terminal or the Run window in GNOME (Alt+F2):
```
albumart-qt
```

You are now good to go find gorgeous album covers! Many thanks to Sami Kyöstilä for this wonderful program. I hope that the project was not taken down at the request of Amazon or Walmart, and that it will be back up and running soon.

---

### Post by Kingfield on 2007-06-10
Thanks soooooo much, you saved me there - thanks =D

---

### Post by mglukhovsky on 2007-06-10
Glad to help. :) Hopefully this will be helpful to others unable to find a copy of this wonderful program.

---

### Post by foxy123 on 2007-07-07
I've got albumart deb, which I downloaded a while ago, so I can upload it somewhere. However I cannot run the programme:
```
~$ albumart-qt
Traceback (most recent call last):
  File "/usr/bin/albumart-qt", line 145, in <module>
    sys.exit(runGui())
  File "/usr/bin/albumart-qt", line 77, in runGui
    import albumart_dialog
  File "/usr/lib/albumart/albumart_dialog.py", line 32, in <module>
    from pixmap import getPixmapForPath
  File "/usr/lib/albumart/pixmap.py", line 4, in <module>
    import albumart_images
  File "/usr/lib/albumart/albumart_images.py", line 6
SyntaxError: Non-ASCII character '\xa0' in file /usr/lib/albumart/albumart_images.py on line 6, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details

```
I have no idea how to fix it. I will try to find the source and compile it as described in the post above.

OK, I found the solution on [http://chopeen.blogspot.com/:](http://chopeen.blogspot.com/:)
```
open the /usr/lib/albumart/albumart_images.py and in the first or second line in the file add:

# coding: latin-1
```

---

### Post by ivago on 2007-07-24
Hi all,

I have installed 1.6 as described above but after downloading  a couple of albums I get the follwoing error

[IMG]http://users.fulladsl.be/spb17723/Error.png[/IMG]

and when I check for details I get;
> Traceback (most recent call last):

  File "/usr/lib/albumart/process.py", line 130, in run
    for cover in albumart.getAvailableCovers(artist, album, requireExactMatch = self.requireExactMatch):

  File "/usr/lib/albumart/albumart.py", line 115, in getAvailableCovers
    results += s.findAlbum("%s %s" % (artist, album))

  File "/usr/lib/albumart/albumart_source_amazon.py", line 48, in findAlbum
    return amazon.searchByKeyword(name,type="lite",product_line="music")

  File "/usr/lib/albumart/amazon.py", line 315, in searchByKeyword
    return search("KeywordSearch", keyword, product_line, type, page, license_key, http_proxy, locale, associate)

  File "/usr/lib/albumart/amazon.py", line 289, in search
    license_key, locale, associate)

  File "/usr/lib/albumart/amazon.py", line 232, in buildURL
    url += "&%s=%s" % (search_type, urllib.quote(keyword))

  File "urllib.py", line 1205, in quote
    res = map(safe_map.__getitem__, s)

KeyError: u'\xe9'

All bi all this code looks exactely what I need to get my folder.jpg automatically in each folder, so I cross my fingers an hope for any suggestions  how to fix this bug... :lolflag:

cheers!

ivago

---

### Post by Kingfield on 2007-11-17
replying to subscribe xP (need it for my new laptop coming)

---

