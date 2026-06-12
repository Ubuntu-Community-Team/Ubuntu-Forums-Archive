---
title: "any good WYSIWYG for editing HTML files?"
date: 2018-06-14
forum: General Help
---

### Post by ardouronerous on 2018-06-14
I'm looking for a WYSIWYG that is similar to KompoZer, I've tried LibreOffice Writer and it was a nightmare to use.

I've used KompoZer when I was still using Windows XP and it was incredible, but KompoZer's latest version is 0.7.10 which is 10 years ago, so it's outdated.

---

### Post by slickymaster on 2018-06-14
[http://bluefish.openoffice.nl/download.html](http://bluefish.openoffice.nl/download.html)

---

### Post by ardouronerous on 2018-06-14
I've installed Bluefish and it's confusing to use, I loaded an HTML file for me to edit and all I'm seeing is HTML scripting, how do I get it to function like KompoZer?

---

### Post by slickymaster on 2018-06-14
Having a read its wiki would be good place to start: [https://bfwiki.tellefsen.net/index.php/Main_Page](https://bfwiki.tellefsen.net/index.php/Main_Page)

---

### Post by ardouronerous on 2018-06-14
I've read the Bluefish manual and it said Bluefish is not a WYSIWYG editor.
[http://bluefish.openoffice.nl/manual/pr01s02.html](http://bluefish.openoffice.nl/manual/pr01s02.html)

---

### Post by walts48 on 2018-06-14
I use Geany, then click the "Run or view the current file" button and the edited page opens in my default browser.

[https://www.geany.org/](https://www.geany.org/)

You can install it from the Ubuntu Software app.

---

### Post by flipper88cfl on 2018-06-14
I've used nano,Leafpad,gedit,mousepad but my favorite of all of them for it's rich feature set is pluma.

sudo apt install -y pluma

---

### Post by dragonfly41 on 2018-06-14
Have you considered the option of writing your content in markdown in an editor such as Atom?

Then you can use pandoc via command line to convert your markdown content into HTML or even HTML slide presentations or PDF (there are many options).

[https://pandoc.org/demos.html](https://pandoc.org/demos.html)

Atom has a markdown preview plugin.

---

### Post by ardouronerous on 2018-06-14
I should have been clearer, I have 0 knowledge on HTML language, so basically, I'm looking for WYSIWYG functionality to Dreamweaver, the closest one is KompoZer, but it is outdated.

---

### Post by PaulW2U on 2018-06-14
Take a look at [SeaMonkey]("https://en.wikipedia.org/wiki/SeaMonkey").

This [screenshot]("https://www.seamonkey-project.org/doc/2.0/img-screen/composer.png") on the SeaMonkey web site clearly shows that Composer has a multi-tabbed interface, one tab is WYSIWYG editing, the others for previews of the HTML source etc.

SeaMonkey Composer is not in the Ubuntu repositories and has to be downloaded from the [SeaMonkey]("https://www.seamonkey-project.org/") website as a .bz2 file and unpacked. The latest release was just last month. It seems that the download comprises a complete suite of applications that include a web browser and email program.

I've never used SeaMonkey myself so can't vouch for any of its claimed capabilities or how well it works with whichever version of Ubuntu you are using. Your choices are very limited and in due course you should learn at least HTML and CSS so you can write the raw code yourself. Hope that helps.

---

### Post by &amp;KyT$0P# on 2018-06-14
Maybe [BlueGriffon]("http://bluegriffon.org/")?

---

### Post by VMC on 2018-06-14
> **halogen2 said:**
> Maybe [BlueGriffon]("http://bluegriffon.org/")?
LOL. Their web page is godawful slow. If this is an indication of there product, no thanks.

---

### Post by ardouronerous on 2018-06-14
> **PaulW2U said:**
> Take a look at [SeaMonkey]("https://en.wikipedia.org/wiki/SeaMonkey").

This [screenshot]("https://www.seamonkey-project.org/doc/2.0/img-screen/composer.png")  on the SeaMonkey web site clearly shows that Composer has a  multi-tabbed interface, one tab is WYSIWYG editing, the others for  previews of the HTML source etc.

SeaMonkey Composer is not in the Ubuntu repositories and has to be downloaded from the [SeaMonkey]("https://www.seamonkey-project.org/")  website as a .bz2 file and unpacked. The latest release was just last  month. It seems that the download comprises a complete suite of  applications that include a web browser and email program.

I've never used SeaMonkey myself so can't vouch for any of its claimed  capabilities or how well it works with whichever version of Ubuntu you  are using. Your choices are very limited and in due course you should  learn at least HTML and CSS so you can write the raw code yourself. Hope  that helps.

That looks like exactly what I need, although I've never installed software via .bz2 before, so I'll have to learn how to install it first. No PPA available?

> **halogen2 said:**
> Maybe [BlueGriffon]("http://bluegriffon.org/")?

Don't I have to pay for that?

---

### Post by &amp;KyT$0P# on 2018-06-14
> **ardouronerous said:**
> Don't I have to pay for that?
Nope, it's a free download.  You *can* choose to pay for extra features, but those features are not required to use the software.

---

### Post by monkeybrain20122 on 2018-06-14
This turned up in a google search. Looks nice. [https://pinegrow.com/](https://pinegrow.com/)

Edited: that is not free apparently.

---

### Post by ardouronerous on 2018-06-14
Thanks for the suggestion, unfortunately, my current PC is 32-bit and BlueGriffon is only available in 64-bit.
Anyway, I have a 64-bit hand-me-down laptop coming through the mail, it will arrive next year and I'll be installing 64-bit Lubuntu 18.04 on it and I'll give BlueGriffon a shot then.

I'll be giving SeaMonkey a shot when I figure out how to install it.

---

### Post by monkeybrain20122 on 2018-06-14
Google web designer? 
[https://www.google.com/webdesigner/](https://www.google.com/webdesigner/)

---

### Post by &amp;KyT$0P# on 2018-06-14
> **ardouronerous said:**
> I'll be giving SeaMonkey a shot when I figure out how to install it.
Just extract the tar.bz2 to your home directory, then run [FONT=Courier New]~/seamonkey/seamonkey[/FONT]

---

### Post by 1clue on 2018-06-14
It's been awhile since I did this, but as of a few years back there were no satisfactory WYSIWYG solutions for HTML, and in my professional opinion there can't be one.

The issue here is that there is more than one browser, more than one operating system. More than one way for markup to work, and then on top of that you have all sorts of plugins and javascript, any of which can affect the rendered page. It's no longer IE vs Firefox, now there's Chrome and who knows what. Look up web browser market share worldwide, and then try to figure out what OS they're using too.

My experience is in making web applications professionally. Meaning I made apps that my company sold to third parties. Every employee in the company used a good programming editor and a collection of browsers, some of which are in VMs. You need to write and test for every platform your customers will use, and every version of browser they are likely to be running. It's tedious. Worse yet, with Linux-based browsers you need to go through several mainstream distros because not every distro uses the same fonts or versions of software. What looks fine on Ubuntu may look like hell on some other distro because those fonts aren't installed by default. Many web applications implement a spreadsheet-like panel where every pixel counts, and tweaking for what looks good on one browser maybe sucks on others.

As well, if you're going to make a sophisticated web app then you can't throw out javascript or many other plugins. There is too much need for client-side code to disable these things. And doing so changes the look of the page as well, because often the javascript is telling the browser which component to draw and where.

The short end of this story is, if you're going to make reliable commercial-grade web application, you need to create your pages intelligently and consistently, and then test it on every browser and operating system combo your customers will use.

---

### Post by mörgæs on 2018-06-15
Following the W3C standards prevents many of the aforementioned problems.

---

### Post by dragonfly41 on 2018-06-15
> [COLOR=#000000]Following the W3C standards prevents many of the aforementioned problems.[/COLOR]

Which brings us to venerable Amaya .. dated but will run on 32bit platform.

[https://www.w3.org/Amaya/](https://www.w3.org/Amaya/)


[COLOR=#b22222]**Correction:**[/COLOR]

The Amaya package is probably too dated now.

Running this to install .. (64 bits version from downloads page)
```
sudo dpkg -i amaya_11.4.4-1_amd64.deb
```
it requires   libssl0.9.8  and   libraptor1

---

### Post by 1clue on 2018-06-15
> **mörgæs said:**
> Following the W3C standards prevents many of the aforementioned problems.

Yes it does. But browser development is not driven by W3C standards, W3C standards are driven by browser development.

---

### Post by bodhin2 on 2018-06-15
i used a great web app Freeway  on macs from england.  100% better than dreamweaver.  they went down the tubes when adobe took them over from macromedia.  when i went 100% linux i also had the problem no serious wysiwyg.  i ended up going with a wordpress that i use through my hosted site.  only a few really basic themes that i liked that did not have a lot of extra garbage on it.  but i have been using for 3 years now.  that was the best work around for me.  i have been dealing with web stuff - no html since mid 90's.  good luck but consider that possibility.

---

### Post by PaulW2U on 2018-06-16
> **dragonfly41 said:**
> The Amaya package is probably too dated now.
Probably a good thing as back in my pre-Ubuntu days I found Amaya to be an interesting piece of software but not one that I would ever want to use.
> **ardouronerous said:**
> That looks like exactly what I need, although I've never installed software via .bz2 before, so I'll have to learn how to install it first.
Hopefully you'll report back and let us know how well SeaMonkey's Composer lived up to your expectations of a WYSIWYG web editor.

---

### Post by dragonfly41 on 2018-06-16
I remember using Freeway years ago on a Mac.  It rendered superb web content as image objects.
 I suggest a similar approach using a desktop publisher, Scribus.
 
 Now one approach is to use SVG editors to get the &#8220;look and feel&#8221; (WYSIWYG)  and then export the SVG object to be embedded within object tags in body of a simple HTML index.html file.
 
 Scribus desktop publishing package is available in Software Centre.
 
 Scribus allows the content to be laid out as you expect to see it.  In document layout, text  and images are placed in multiple frames and the properties of each frame can be set in panels.   
 
 After completing the layout, Scribus offers export of created document to formats such as SVG (but not HTML). You can also export content as PDF or ebook.
 
 Note that when embedding the svg file into HTML the top header (up to the opening tag svg ) should be removed since this is  in the HTML header.
 
 SVG objects can then be embedded in a simple HTML index.html file using object tags.
 
 To learn more about basics go to w3schools.com

 One disadvantage of using embedded SVG is the text of the web site is in svg format cannot be indexed by search engines such as google. Embedded SVG is not compatible with Search Engine Optimisation (SEO) if you hope to rank your web pages.
 
 On the other hand the SVG fonts are very smooth and anti-aliased. SVG is a W3 standard.
 
 And the Scribus content can be exported into PDF and ebook formats for publication.

 Here is just one article supporting the use of SVG ...
 
 [https://www.1and1.co.uk/digitalguide/websites/website-creation/svg-format-how-to-embed-svg-vector-graphics/](https://www.1and1.co.uk/digitalguide/websites/website-creation/svg-format-how-to-embed-svg-vector-graphics/)

---

### Post by ardouronerous on 2018-06-16
> **PaulW2U said:**
> Hopefully you'll report back and let us know how well SeaMonkey's Composer lived up to your expectations of a WYSIWYG web editor.

I've just installed it and it's good.
But it's kinda annoying that I have to go through the Seamonkey Browser to get to the Composer, is there anyway to create a desktop link to the Composer itself?

Question, what's the difference between Firefox and Seamonkey?
It seems Seamonkey is connected to Firefox, seeing that it used the .mozilla folder to store it's profile.

Okay, I figured it out through here: [http://netscape.public.mozilla.seamonkey.narkive.com/sBEtME6z/launch-seamonkey-in-composer-mode](http://netscape.public.mozilla.seamonkey.narkive.com/sBEtME6z/launch-seamonkey-in-composer-mode)

```
[Desktop Entry]
Version=1.0
Type=Application
Name=SeaMonkey Composer
Comment=WYSIWYG HTML editor
Icon=/home/~/.seamonkey2/seamonkey/chrome/icons/default/editorWindow48.png
Exec=**/home/~/.seamonkey2/seamonkey/seamonkey -editor**
NoDisplay=false
Categories=Network;
StartupNotify=false
Terminal=false
```

Question, how do I keep Seamonkey up to date though?
Or does it update itself?

Okay, weird things began happening to my system after I installed and used Seamonkey Composer.

When I tried to extract files to Desktop from a zip file, PCManFM says Desktop has 0 files, but when I viewed Desktop in Thunar, it says there are files there. Also, when I rebooted my system, my desktop preferences were reverted back to it's default settings.

At the moment, I've deleted SeaMonkey because of this weird behavior.

---

### Post by CharlesA on 2018-06-17
> **ardouronerous said:**
> 
Question, how do I keep Seamonkey up to date though?
Or does it update itself?

I don't know if it has a built-in updated, but as you are running it as a standalone binary, you can just download it and extract it to a folder.

> **ardouronerous said:**
> Okay, weird things began happening to my system after I installed and used Seamonkey Composer.

When I tried to extract files to Desktop from a zip file, PCManFM says Desktop has 0 files, but when I viewed Desktop in Thunar, it says there are files there. Also, when I rebooted my system, my desktop preferences were reverted back to it's default settings.

At the moment, I've deleted SeaMonkey because of this weird behavior.

Make sure you are in the correct "Desktop" folder. It should be in /home/username/Desktop

---

### Post by ardouronerous on 2018-06-17
> **CharlesA said:**
> Make sure you are in the correct "Desktop" folder. It should be in /home/username/Desktop

Yes, that is the folder where Desktop is.

I have to suspect SeaMonkey because I've never experienced this weird behavior before, it only happened after I installed and used SeaMonkey.

Things seems to be back to normal after I removed SeaMonkey from my system.

---

### Post by dragonfly41 on 2018-06-17
At least give the Scribus idea a try (post #25 above)

To install ...

```
sudo apt-get install scribus-ng
```

or if you prefer a daily build (daily upgrades)

```
sudo apt-get install scribus-trunk
```

---

### Post by ardouronerous on 2018-06-17
I tried Scribus and I can't load the HTML files that I want to edit.

---

### Post by dragonfly41 on 2018-06-17
But in post #9 you wrote ..
> [COLOR=#000000]I should have been clearer, I have 0 knowledge on HTML language, so basically, I'm looking for WYSIWYG functionality to Dreamweaver[/COLOR]

With Scribus and other such tools you start with raw text to drop into text frames.

---

### Post by ardouronerous on 2018-06-17
Yes, but Dreamweaver and KompoZer allows me to open any html files and lets me edit them, this is my initial purpose, sorry if I wasn't clear about that, that is the purpose of me looking for software with similar functionality to Dreamweaver.

---

### Post by dragonfly41 on 2018-06-17
First point of clarification.  Scribus is intended for publishing quality documents (without interactive scripting and hyperlinks) and it may not fit every web site designer's goal since its prime purpose is to publish documents not web sites.   However if interactivity is required this can be added later to elements in the exported SVG code and/or to the wrapper html file in which SVG is embedded.

HTML can be imported into Scribus as explained here ...

[http://write.flossmanuals.net/scribus/importing-text-and-images/](http://write.flossmanuals.net/scribus/importing-text-and-images/)


This is how I did it.

Create new page in Scribus.

Create text frame.

Select the text frame (the blinking cursor is inside the text frame).

File > Import > Get Text

In the popup panel select the *.html file to be imported into your text frame, 
choose Files of type: HTML, and alongside Importer tick Import Text Only.

This will scrape the text from your HTML file and place it in the text frame.

...

[COLOR=#b22222]**[Later edit]**[/COLOR]

However this does not allow editing of the source HTML file which you might want.

For this I would revert to using markdown with pandoc, and an editor such as Atom (plus markdown preview plugin).

Your existing HTML files can be converted into markdown using pandoc API.

---

### Post by ardouronerous on 2018-06-17
Can Scribus handle tables of information?
The HTML files that I want to edit has tables, similar to a calendar.

I've tried LibreOffice Writer, it didn't handle the tables well.

But to use Atom, I have to learn how to code in HTML right?

Is there an online service that allows me to upload HTML files and edit them online?

---

### Post by dragonfly41 on 2018-06-17
Tables

[https://wiki.scribus.net/canvas/Import_Spreadsheet_Tables_to_Scribus](https://wiki.scribus.net/canvas/Import_Spreadsheet_Tables_to_Scribus)

[https://wiki.scribus.net/canvas/Table_implementation](https://wiki.scribus.net/canvas/Table_implementation)

[https://pandoc.org/try/](https://pandoc.org/try/)

In this demo drag one of your HTML files to the left panel and choose from HTML
then in right panel choose  Markdown (pandoc).

[https://pandoc.org/](https://pandoc.org/)

Atom editor can be used to write your content in markdown and you can preview what it looks like in HTML through the Markdown Preview plugin.

[https://github.com/atom/markdown-preview](https://github.com/atom/markdown-preview)

In Markdown you can also write tables.

[https://atom.io/](https://atom.io/)

---

### Post by ardouronerous on 2018-06-17
Okay, I tried Scribus again and it doesn't really look good to me, sorry.
And to use Atom, I have to learn to write in Markdown language.

Again, any online services that can allow me to edit HTML files from the browser?

---

### Post by dragonfly41 on 2018-06-17
"You can take a horse to water but you can't make it drink".

Regarding on line html editors there are loads but I will not choose one. 
Just google "online html editors".

---

### Post by ardouronerous on 2018-06-17
Sorry, just didn't like how Scribus looked and the work needed to get my desired result, sorry if I offended you.

Yeah, I googled it and there's lots of online html editors, reason why I'm asking for suggestions is because I don't want to choose a fake one.

---

### Post by dragonfly41 on 2018-06-17
I'll give it another shot.
Personally I would avoid online editors.

Instead, install cherrytree from Software Centre.

When creating your first cherrytree document save in XML Not protected format (not SQL)
in some convenient folder.  Avoids complexity of encryption.

Add a top level node (I usually name it Root).

Add a sub-node (page1 in your web site)

Now go to Import > From HTML File.

You can create a hierarchy of nested nodes (pages).

To export document go to Export > Export to HTML

You might create a node for each web page.

To insert tables into nodes go to Edit > Insert table.
You can import tables from csv.

To create an index page go to Edit > Insert TOC.

I use CherryTree on a daily basis for many uses.
You can also embed HTML in a codebox in any node.

---

### Post by #&amp;thj^% on 2018-06-17
> **ardouronerous said:**
> 


Question, how do I keep Seamonkey up to date though?
Or does it update itself?

.

I truly don't want this to add to your confusion/frustrations>> How to Install SeaMonkey on Ubuntu and keep it updated

SeaMonkey isn’t included in Ubuntu repository. but we can install SeaMonkey via Ubuntuzilla, which is an APT repository containing the latest SeaMonkey deb package.

To add the Ubuntuzilla repository to your system, you need to open up a terminal window and edit the sources.list file.
```

sudo nano /etc/apt/sources.list
```

Then scroll down to the bottom of the file and append the following line into the file.
```

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

Save and close the file. Then run the following command to import Ubuntuzilla public key to your GPG keyring so that the integrity of packages downloaded from this repository can be verified by APT.
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2667CA5C
```
I beleive that this key is still valid.

Finally, update your package list and install SeaMonkey.
```

sudo apt-get update
```
Show us any errors if any.
If there is none install with:
```

sudo apt-get install seamonkey-mozilla-build
```

Once installed, you can start it from the Menu or your application launcher.
If for any reason you want to remove it, use this command:

```
sudo apt-get remove seamonkey-mozilla-build
```
And remove the PPA from your "/etc/apt/sources.list"

That’s it!

---

### Post by bodhin2 on 2018-06-17
again not to pile on - check out wordpress.  it works great for me.  sure maybe the color palette is a bit bland but everything is laid out perfectly for my needs.

also even with marcomedia - problem with dreamweaver is that all tweaks add to the code and then garbages it all up after a while - freeway generates total new code even for adding a period as such.

you can work wordpress through your isp and do it in your browser or install it if needed and then upload - i do the first - easier.

---

### Post by CharlesA on 2018-06-17
> **bodhin2 said:**
> again not to pile on - check out wordpress.  it works great for me.  sure maybe the color palette is a bit bland but everything is laid out perfectly for my needs.

also even with marcomedia - problem with dreamweaver is that all tweaks add to the code and then garbages it all up after a while - freeway generates total new code even for adding a period as such.

you can work wordpress through your isp and do it in your browser or install it if needed and then upload - i do the first - easier.

This could work, but for the love of everything, keep it updated and choose your plugins carefully.

---

### Post by ardouronerous on 2018-06-17
> **dragonfly41 said:**
> Instead, install cherrytree from Software Centre.

I've tried CherryTree, not really to my liking sorry.

> **1fallen said:**
> I truly don't want this to add to your confusion/frustrations>> How to Install SeaMonkey on Ubuntu and keep it updated

SeaMonkey isn’t included in Ubuntu repository. but we can install SeaMonkey via Ubuntuzilla, which is an APT repository containing the latest SeaMonkey deb package.

To add the Ubuntuzilla repository to your system, you need to open up a terminal window and edit the sources.list file.
```

sudo nano /etc/apt/sources.list
```

Then scroll down to the bottom of the file and append the following line into the file.
```

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

Save and close the file. Then run the following command to import Ubuntuzilla public key to your GPG keyring so that the integrity of packages downloaded from this repository can be verified by APT.
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2667CA5C
```
I beleive that this key is still valid.

Finally, update your package list and install SeaMonkey.
```

sudo apt-get update
```
Show us any errors if any.
If there is none install with:
```

sudo apt-get install seamonkey-mozilla-build
```

Once installed, you can start it from the Menu or your application launcher.
If for any reason you want to remove it, use this command:

```
sudo apt-get remove seamonkey-mozilla-build
```
And remove the PPA from your "/etc/apt/sources.list"

That’s it!

I was a little hesitant at install SeaMonkey again, after my system began to act weird after install and usage.
Anyway, I gave this a shot, installing SeaMonkey through Ubuntuzilla and it works well, it didn't give my system problems at all.

Why did the .bz2 version of SeaMonkey give my system grief, but the Ubuntuzilla didn't? Weird.

---

### Post by #&amp;thj^% on 2018-06-18
> **ardouronerous said:**
> 

Why did the .bz2 version of SeaMonkey give my system grief, but the Ubuntuzilla didn't? Weird.

The .bz2 **"in my opinion"** is to run a stand alone model and sometimes depending on the DE used dose not intergrade with the system well enough.
This seamonkey from the PPA is built to mesh nicely with the system.
I'm happy to hear that you are having no problems with the install though. :)

---

### Post by ardouronerous on 2018-06-18
Yes, I'm quite happy with SeaMonkey Composer, it's everything I could ever hope for in a WYSIWYG HTML editor.

I just hope SeaMonkey doesn't become like KompoZer, unmaintained and undeveloped.

Lesson learned, never install via .bz2, always install through .deb file or PPA.

Thanks for the help!

---

### Post by walts48 on 2018-06-18
> **ardouronerous said:**
> I've tried CherryTree, not really to my liking sorry.



I was a little hesitant at install SeaMonkey again, after my system began to act weird after install and usage.
Anyway, I gave this a shot, installing SeaMonkey through Ubuntuzilla and it works well, it didn't give my system problems at all.

Why did the .bz2 version of SeaMonkey give my system grief, but the Ubuntuzilla didn't? Weird.

Did you download and install the SeaMonkey 32-bit build or the 64-bit contributed build?

[https://www.seamonkey-project.org/releases/#contrib](https://www.seamonkey-project.org/releases/#contrib)

I prefer the contributed build over the Ubuntuzilla build, because it is exactly the same, and I don't have to wait for it to show up in the repository.

---

### Post by dragonfly41 on 2018-06-18
Just for good measure ..

here is a clip of Scribus (svg) export rendered in SeaMonkey.

---

### Post by 1clue on 2018-06-18
> **dragonfly41 said:**
> Just for good measure ..

here is a clip of Scribus (svg) export rendered in SeaMonkey.

The problem with this approach is that you lost the text. It means the page will be formatted to fit exactly one screen size, whether you're on a phone or a tablet or a laptop or a 4k desktop display. Whether your client has primitive font rendering or the best there is, it's all the same.

You lose the ability to highlight a word or phrase and look it up in your favorite search engine. You lose the abliity to go to a text mode like smart phones can do, where it removes everything except the story text when using html5.

Also WRT a GUI editor, so far as I have ever noticed, when you use a GUI html editor your output page is completely unreadable by a human and therefore the only way you will ever edit it is by opening it in a gui editor again, and hope all the same features are supported in the same way as they were last time you saved it.

WRT either GUI editor or graphical pre-rendering of the page, you also pretty much eliminate the possibility of source code control providing any reasonable change log.

---

### Post by dragonfly41 on 2018-06-18
For some applications it  can be useful to prevent visitors scraping your web text content (although ocr can be applied).

Regarding dynamically matching content to devices that is easily built in.

But I accept that this approach is an outlier.

---

### Post by 1clue on 2018-06-18
So, android phone with X*Y resolution, but 5 different font sizes and who knows how many default fonts? And remember this is for each viable resolution. And then iphones, and then tablets of various sizes, and then laptops of various sizes....

As a general rule if I'm producing content I want that content to be read, and very likely I want it indexed by search engines. And likely people may want to automatically translate the text to their native language.

While I can understand the ideas you're putting out, I think there are better ways to achieve all of them than by rendering the text to an image and then posting that image instead of text.

I don't intend to go on about it, I think I made my point.

---

### Post by ardouronerous on 2018-06-19
> **walts48 said:**
> Did you download and install the SeaMonkey 32-bit build or the 64-bit contributed build?

[https://www.seamonkey-project.org/releases/#contrib](https://www.seamonkey-project.org/releases/#contrib)

I prefer the contributed build over the Ubuntuzilla build, because it is exactly the same, and I don't have to wait for it to show up in the repository.

My system is Lubuntu 16.04 LTS 32-bit.

I downloaded the .bz2 from here: [URL="https://www.seamonkey-project.org/releases/#MainDownloads"]https://www.seamonkey-project.org/releases/#MainDownloads
[/URL]
> **dragonfly41 said:**
> Just for good measure ..

here is a clip of Scribus (svg) export rendered in SeaMonkey.

As 1clue had said, the drawback to this method is that I cannot select the text from the HTML normally this way, I usually employ a TTS reader to read clipboard for me, so your method would make that difficult, and also, my work wouldn't be able to be indexed by search engines, so there's that.

---

### Post by registrazioni-h on 2019-02-18
Many pages to read, but...
I've just installed SeaMonkey.
The Composer is GREAT!
Exactly what I need: simple, robust and effective.
Thank you all!

---

### Post by serendipitydavies on 2020-01-16
> **registrazioni-h said:**
> Many pages to read, but...
I've just installed SeaMonkey.
The Composer is GREAT!
Exactly what I need: simple, robust and effective.
Thank you all!

Thank you too, I have installed SeaMonkey as well :)
Have been looking for a WYSIWYG editor for ages until I found this thread.
It's the first program I've ever installed using the Terminal!

---

### Post by ajgreeny on 2020-01-16
I have never so far tried seamonkey, nor used it from either a .deb install or simply by running the executable from the downloaded .tar.bz.

I have, however, used firefox as the .tar.bz archive in an installation of Debian 10 which does not have the "real" firefox in its repos, only the firefox.esr version. In DEbian 10 the version updates itself automatically if there's an update available when you start it.  I'm not sure if that is a user setting in the preferences, but it certainly has worked without a problem so far, though the auto-update surprised me somewhat.

---

