---
title: "Issue with wkhtmltopdf"
date: 2023-09-17
forum: General Help
---

### Post by sed_faster on 2023-09-17
I was try run this command with respectively parameters:

```

wkhtmltopdf --enable-local-file-access -s A4 --footer-html "footer.html" --margin-top 50 --margin-bottom 10 --margin-left 3.5 --margin-right 3.5 --footer-line --footer-right "Page [page] of [topage]" --footer-font-size 6 content.html content.pdf

```

The goal is add footer.html in bottom of the page content.html with respectively parameters margin setup. When I executed the command I got this message:

> 
The switch --footer-html, is not support using unpatched qt, and will be ignored.
The switch --footer-line, is not support using unpatched qt, and will be ignored.
The switch --footer-right, is not support using unpatched qt, and will be ignored.
The switch --footer-font-size, is not support using unpatched qt, and will be ignored.

Loading page (1/2)
Printing pages (2/2)
Done


I can got the conversion to pdf from html but the parameters mention on error message didn't acceptable or ran. Nor footer.html was add in bottom on content.html page.
I searched about how could I solve this issue and found this website: [https://gist.github.com/faniska/37f896d5e9de5fee925925d7caf3cb9e](https://gist.github.com/faniska/37f896d5e9de5fee925925d7caf3cb9e)

I checked my wkhtmltopdf and qt version:

```

wkhtmltopdf -V wkhtmltopdf 0.12.6

[FONT=monospace][COLOR=#000000]qmake --version [/COLOR]
QMake version 3.1 
Using Qt version 5.15.3 in /usr/lib/x86_64-linux-gnu[/FONT]

```

The instruction, from [https://gist.github.com/faniska/37f896d5e9de5fee925925d7caf3cb9e](https://gist.github.com/faniska/37f896d5e9de5fee925925d7caf3cb9e) are:

```

# Uncomment the next line if you have installed wkhtmltopdf
# sudo apt remove wkhtmltopdf
cd ~
# Select an appropriate link for your system (32 or 64 bit) from the page https://wkhtmltopdf.org/downloads.html and past to the next line

wget https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz
tar xvf wkhtmltox*.tar.xz
sudo mv wkhtmltox/bin/wkhtmlto* /usr/bin
sudo apt-get install -y openssl build-essential libssl-dev libxrender-dev git-core libx11-dev libxext-dev libfontconfig1-dev libfreetype6-dev fontconfig

```

The version I has install in my system is 0.12.6, according to this website is the lasted and more updated version available: [https://github.com/wkhtmltopdf/wkhtmltopdf/releases](https://github.com/wkhtmltopdf/wkhtmltopdf/releases)
They, in [https://gist.github.com/faniska/37f896d5e9de5fee925925d7caf3cb9e](https://gist.github.com/faniska/37f896d5e9de5fee925925d7caf3cb9e) advise me to reverse my wkhtmltopdf version to 0.12.4

My doubts is two:


[LIST=1]
[*]Is this a good way to solve my issue?
[*]Should I trust in a git repository as much as I trust in my "sudo apt-get install wkhtmltopdf"?
[/LIST]

I am a newbie and I really concern about security issues. And I always prefer install software through this program "apt-get". I know than the suggest/purporse I found to solve the problem suggest me to downgrade the version software wkhtmltopdf to solve the issue but I don't know if I am doing something dangerous or installing something harmful to my environment following this steps: [https://gist.github.com/faniska/37f896d5e9de5fee925925d7caf3cb9e](https://gist.github.com/faniska/37f896d5e9de5fee925925d7caf3cb9e)

```

[FONT=monospace][COLOR=#000000]apt-cache search wkhtmltopdf[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]wkhtmltopdf - Command line utilities to convert html to pdf or image using WebKit[/COLOR]
[/FONT]
```

The manual to the wkhtmltopdf software you could read on this link: [https://wkhtmltopdf.org/usage/wkhtmltopdf.txt](https://wkhtmltopdf.org/usage/wkhtmltopdf.txt)

Thank you

---

### Post by dragonfly41 on 2023-09-18
If you favour using only apt then I suggest that you install Synaptic Package Manager.
I am still using Ubuntu 20.04 and when I launch Synaptic Package Manager and search "wkhtmltopdf" I see ..
wkhtmltopdf  0.12.5
and also python3 wrapper
python3-pdfkit
Python wrapper for wkhtmltopdf to convert HTML to PDF (Python 3)


But if you wish to try alternative tools to merge html files and convert to PDF
there are other workflows to try ..

[pandoc]("https://pandoc.org/") is recommended for such purpose of document conversion  ..
or you might fall back to writing content in Markdown then exporting to PDF.

Several editors you can try (I use these).
Zettlr
Sublime Text
CherryTree
Scribus

Much depends on the volume and complexity of work you have in mind.

wkhtmltopdf might be quite adequate for your purposes but you might learn how to use the other tools for other jobs.  Perhaps try the python3 wrapper.  Often I use a toolchain .. several tools in a pipeline.

Github source is usually safe since source is open to scrutiny if insecure commands are published.

---

