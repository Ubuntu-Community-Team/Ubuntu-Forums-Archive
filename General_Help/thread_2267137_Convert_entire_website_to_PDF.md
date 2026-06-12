---
title: "Convert entire website to PDF"
date: 2015-02-27
forum: General Help
---

### Post by sofasurfer on 2015-02-27
Found tons of PDF converters but can not find a site or package to convert a website to PDF for reading on the road. Can you help?

---

### Post by Lars Noodén on 2015-02-27
wget has, in addition to spidering capabilities, the ability to convert links and download files that are necessary to properly view a page.  See -k, -p, and -w in addition to -l and -m .  However, most sites take poorly to spidering and will ban your ip if it is done too inconsiderately.  Some sites will ban your ip if it looks even a little like spidering.

That would allow you to read HTML offline

---

### Post by sofasurfer on 2015-02-28
I found that wget will download the website as html files. It functions just as the original website did. I then found that the program "wkhtmltopdf" will convert the html files to pdfs. However, when I finished with this step and I had all of the files converted to pdfs, NONE of the links work and so navigating is impossible by clicking. Any idea what went wrong?

---

### Post by Lars Noodén on 2015-02-28
Did you try wget with -k to convert the links to relative links for local viewing?  What were the exact options you used to download and then convert to PDF?

---

### Post by sofasurfer on 2015-02-28
I used the instructions on this site. [http://darrennewton.com/2011/10/30/mirror-site-and-convert-to-pdf/](http://darrennewton.com/2011/10/30/mirror-site-and-convert-to-pdf/)
I had to change a couple things to fit my needs such as paths.
My wget command did NOT include "-k". I'll try again tomorrow. Is this needed since my links in the files created by wget are working fine? It is only in the pdf files created with wkhtmltopdf that the links do not work.
I'll do the process again tomorrow and see what happens.

I think I just saw the answer to my question about the "-k" switch. Thelinks in the html files take mr to the web, not another file. So the "-k" is the answer,right?

---

### Post by Lars Noodén on 2015-02-28
If the links in the HTML files are fine then there would be no need to change how you use wget, I think.  The guide uses the long versino of -k which is --convert-links.  The problem then lies with wkhtmltopdf, so no need to download the HTML again.  Ufortunately the guide there does not say much about the converter.  Have you tried looking at the options to see if anything looks like it might be useful?  I see some about enabling or disabling internal and external links:

[http://wkhtmltopdf.org/usage/wkhtmltopdf.txt](http://wkhtmltopdf.org/usage/wkhtmltopdf.txt)

---

### Post by nerdtron on 2015-02-28
there's probably a firefox extension for this.

---

### Post by Bucky Ball on 2015-02-28
There's at least one. [Web2PDF Converter.]("https://addons.mozilla.org/en-US/firefox/addon/web2pdf-converter/") Firefox>Tools>Add-ons>Search for it and install. I'm curious to see if it works OK. Could be handy. ;)

---

### Post by nerdtron on 2015-02-28
Another one I use, well not for reading, but for capturing the whole webpage is Nimbus Screenshot add on for firefox which can capture the whole web page and save it as an image.

---

### Post by sofasurfer on 2015-02-28
Ok, I'm going to repeat the process step by step and explain what I do and what I get.

```
$ mkdir /home/daryl/Documents/wget

s$ wget --mirror -w 2 -p --html-extension --convert-links -P /home/daryl/Documents/wget [http://nameofwebsite.com/](http://nameofwebsite.com/)
```

The result is a folder with jpeg images and a folder of documents and files ending in "html" and "htm". Clicking a file opens the web page and all links work properly. But I think that when I open the site it is acyually on line and not just my files. Is this correct or not?

Now I do this

```
find /home/daryl/Documents/wget/nameofwebsite.com -name '*.html' -exec wkhtmltopdf {} {}.pdf \;
```

The result is that all of the html files have been reproduced as pdfs and all are listed.

Next

```
find /home/daryl/Documents/wget/nameofwebsite.com -name '*.htm' -exec wkhtmltopdf {} {}.pdf \;
```

The result is that the same is done with htm files.

Should I go into the folders and also convert the images and documents?

At this point, when clicking on the created pdf files, the links do not work.

Now I do this

```
mkdir /home/daryl/Documents/wget/pdfs
```

And finally

```
find /home/daryl/Documents/wget/nameofwebsite.com -name '*.pdf' -exec mv {} /home/daryl/Documents/wget/pdfs/ \;
```

Same as before. No working links.

---

### Post by sofasurfer on 2015-02-28
I did some google searches for "wkhtmltopdf links not working" and got plenty of information that seems to indictate that there is some programing corrections that need to be made to wkhtmltopdf.(beyond my abilities) However, the site that explains how to create the pdfs, using wkhtmltopdf, seems to indicate that the links work since he has a link at the bottom of his page that takes you to his pdf with working links. 
I obtained my wkhtmltopdf package from synaptic package manager.

---

### Post by Bucky Ball on 2015-02-28
Please use code tags for terminal output. See the last link in my thread for how. Thanks. ;)

---

