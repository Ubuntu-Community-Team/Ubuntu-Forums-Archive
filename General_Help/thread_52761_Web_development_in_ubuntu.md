---
title: "Web development in ubuntu"
date: 2005-07-28
forum: General Help
---

### Post by OneSeventeen on 2005-07-28
Right now I'm used to dreamweaver mx 2004 in code view for writing PHP based web applications.

I really don't need a wysiwyg editor, but I'm very huge on color coding, and if at all possible, code hints.

I just want some suggestions on what software to use, and maybe some techniques for managing the local and remote files (I really like editing a local copy then uploading it to the file server, but I'd rather not have to navigate folders every time I change a file.)

I would also prefer tools that are available via synaptic if at all possible.

---

### Post by cka on 2005-07-28
gedit can colour highlight syntax for a bunch of languages (but that's all though, no suggestion/intellisense type stuff or code folding afaik), and a really handy feature in gnome is mapping folders to ftp addresses and such so you can browse your server's public_html directory in nautilus as if it were a local directory on your filesystem.  IDEs I'm not so sure about, but I'm fairly certain there's at least some in the repositories...

---

### Post by Omnios on 2005-07-28
Theres Nvu think I got it from synaptic backports its like a lot of other win web developer stuff. Looks pretty sweet as far as html editors go.

---

### Post by OneSeventeen on 2005-07-28
Unfortunately I haven't figured out how to make nvu allow me to download existing files, it only lets meupload edited files.  (that and the copy I got, when I tried saving a file after editing the source, all of the changes disappeared.)

But that may just be because I didn't know how to use the program.

When mapping folders, can you choose how files are transferred?  (i.e. .pdf files transferred binary and .php files ascii?)

I'm willing to give up the luxury, but I am still interested if anyone knows how to upload files in ubuntu and have an app choose where to put things.  (i.e. ~/mysite/ would be the root folder, so if I wanted to upload ~/mysite/htdocs/index.php it would upload it to my remote [ftp://htdocs/index.php](ftp://htdocs/index.php))

---

### Post by dare2dreamer on 2005-07-28
Have a look at bluefish. It's an excellent html/source editor and is already in the ubuntu repositories.

---

### Post by OneSeventeen on 2005-07-28
I haven't gotten bluefish to manage the content though... does it have any fp stuff built in?

(It looks good other than that though!)

---

### Post by cka on 2005-07-28
[QUOTE=OneSeventeen]
When mapping folders, can you choose how files are transferred?  (i.e. .pdf files transferred binary and .php files ascii?)
[/QUOTE]

It *should* determine automatically depending on what the mime type is set to.  I've uploaded both ascii and binary files to my servers using mapped folders without any issue...

---

### Post by auburn on 2005-07-28
I use bluefish when I'm not using VIM. I coudn't get nvu to run. (I think I followed the directions on ubuntuguide.org 'bout 1/ 2 a year ago.) I use gftp with its bookmarks to upload and download. 
Bluefish and NVU are the closest to dreamweaver. 
You could also install firefox extensions for code editors and fireftp (a firefox extension). 

But vim (and probably emacs-which I don't know) is the old standard, ultimate in custamizability, editor. It's available on all *nixs. It's also nice b/c it keeps you on the command line if your'e comfortable there. VIM, I was taught, is known to be "user-hostile" because of it's initial steep learning curve. But it has a really powerful and unique interface. You can tell it's the product of coding shortcuts developed over the past several decades. It *feels* wise. It uses regular expressions innately. It allows you to avoid the mouse (efficient). And there are tons of scripts you can add to your ~/.vimrc. The official site has 1,300. Oh, and yes, color coding is definitely available.

beginner reference:
[http://www.fprintf.net/vimCheatSheet.html](http://www.fprintf.net/vimCheatSheet.html)
some html specific scripts:
[http://www.infynity.spodzone.com/vim/HTML/](http://www.infynity.spodzone.com/vim/HTML/)
the vim site's 1300 scripts:
[http://www.vim.org/scripts/index.php](http://www.vim.org/scripts/index.php)

---

### Post by MaBu on 2005-07-31
Try Scite, it can be connected with PHP Manual and when you highliht a word it shows the manual.

Or Try Quanta +

---

### Post by j0e on 2005-07-31
I use jEdit and find that the colour highlighting works far better than that in gEdit and Bluefish (which seems to go wrong sometimes). You can very easily install the FTP plugin that allows you to work on files remotely.

I'd always been hesitant about trying it out (assuming it was aimed towards Java developers - not at all the case AFAIK), but I'm really impressed with it. Well worth trying. :)

---

### Post by SuperMike on 2005-07-31
I'm surprised no one has said anything about Screem. It's like right there in Add/Remove Programs as if the makers of Ubuntu want you to use it. And this is the best Screem I've seen on any distro. Sure, I used to be a big fan of Quanta+, but Screem has passed these expectations. I then download the extended chm version of help from php.net and combine that with the xchm package -- giving me a fantastic help program for PHP.

Some of my desired changes I make in the default Screem are:

* Change Blank Document Type in Preferences, Misc, to PHP Script.
* Change DocType in Preferences, Misc, to -//W3C//DTD HTML 4.01 Transitional//EN.
* Set editor font in Preferences, Fonts & Colors to Monospace 8.
* Set tabs to 4 characters wide in Preferences, Editor.
* Uncheck Error Highlighting and Wrap Lines in Preferences, Editor.
* Check Autoindent Based off Document Tree in Preferences, Editor.
* Uncheck Intelligent Tag Closing in Preferences, Editor.
* Uncheck Show Function Definition Tooltips in Preferences, Editor.
* Don't show the Wizard toolbar.
* On View, Dock Items, only show Files and Resources.
* Click Site, Open, and find my website I want to work with. This changes my Files tree so that it only shows the website I want to work on, not the entire directory from /.

David A. Knight, creator of Screem, ranks right up there now with the GNOME Mega Gods, as far as I'm concerned.

---

### Post by OneSeventeen on 2005-08-11
Have any of you used Zend Studio?
I'm tempted to purchase it, but I can't tell a whole lot about it from the screenshots it  gives, and I wanted to know how well it works in ubuntu.

---

### Post by OneSeventeen on 2005-08-21
Okay, I tried screem the other day, and it actually seemed pretty cool.

It even offered up all the mysql functions after I typed mysql_, then Ijust scrolled to what I needed, and hit enter, then it told me all the values I could pass that function.

Now that I decided to use screem, I went in, set up a site, told it my ftp info, and when I type PHP it doesn't do a thing... no color coding, no code tips, no nothing!

I have not changed anything that I know of that could possibly tell it to ignore PHP.  Any tips?

If anyone has better apps that are in the ubuntu repositories, please let me know.  (I have enabled all the extra repositories.)  I don't really care what I use, as long as it offers color coding and code tips.

---

### Post by David A Knight on 2005-08-23
Colour coding and tips will only appear if screem knows it is a php file. 

If you just start typing a new file screem by default treats this as an html document.  the button on the statusbar will let you change this on a document basis,  the default can be changed in the preferences.

It is also possible that the file appears to gnome-vfs as an html file due to the way mime type sniffing works.  In this case all you can do is use the button in the statusbar.

---

### Post by jeffreyvergara.NET on 2005-09-27
hello, is there any Web Developement Software for Ubuntu Linux with FTP support other than NVU? I really like the feature of Dreamweaver MX 6 to 2004 but it seems it can't be run in Linux even though you use Cedega, Crossover Office and Wine in istalling DMX6.0

---

### Post by primeirocrime on 2005-09-27
there is gPHPedit in synaptic

---

### Post by n0ah on 2005-12-05
[QUOTE=j0e]I use jEdit and find that the colour highlighting works far better than that in gEdit and Bluefish (which seems to go wrong sometimes). You can very easily install the FTP plugin that allows you to work on files remotely.

I'd always been hesitant about trying it out (assuming it was aimed towards Java developers - not at all the case AFAIK), but I'm really impressed with it. Well worth trying. :)[/QUOTE]


Thank you so very very very much! I've been looking for something this robust and useful since I fully switched from windows, you're a life-saver.

It runs so slick, and with the plugins available it's my new best friend (aside from you obviously)

Web-dev in asp for clients is a bitch to do without syntax highlighting (I'm a wuss I know..), and none of the other linux web-dev software do that.. 

Thanks a million..

-D

---

### Post by David A Knight on 2005-12-05
[QUOTE=n0ah]
Web-dev in asp for clients is a bitch to do without syntax highlighting (I'm a wuss I know..), and none of the other linux web-dev software do that.. 
-D[/QUOTE]

screem does, as does any other gtksourceview using editor (gedit etc.)

dunno how good the highlighting is though as I don't do asp, or have any asp files.

---

### Post by dakine on 2005-12-05
If you are serious about web development than I would highly recomend Eclipse ([http://www.eclipse.org](http://www.eclipse.org)) and use the PHP plugin from [http://phpeclipse.de](http://phpeclipse.de).

"Eclipse is an open source community whose projects are focused on providing a vendor-neutral open development platform and application frameworks for building software. The Eclipse Foundation is a not-for-profit corporation formed to advance the creation, evolution, promotion, and support of the Eclipse Platform and to cultivate both an open source community and an ecosystem of complementary products, capabilities, and services."

dakine

---

### Post by Naneau on 2005-12-12
I'm used to Dreamweaver as well. It's a very heavy program if you just want to use the code editor, but I was never able to get the hang of editors like JEdit, UltraEdit and whatever on windows. After a bit of experimenting on Ubuntu I found that Quanta was my kind of thing, it just... feels right. It has all the things you  need, and a lot more. If you're just after an editor for PHP you don't need it's complicated but powerful project management, or other functions, there are alternatives that are a bit more... lightweight. 

I've tried Screem, and liked it, but I still prefer Quanta, but that's a personal thing, I also prefer KDE over GNOME, though both have their pros and cons. You probably should try at least Screem and Quanta, they are both highly functional specialized Webdevelopment IDE's. There are a **lot** of other editors that have some support for php/html in one way or another for linux though.

> It even offered up all the mysql functions after I typed mysql_, then Ijust scrolled to what I needed, and hit enter, then it told me all the values I could pass that function.

you can get that behaviour in Quanta (and some other editors that I know of), by pressing ctrl+space (by default), auto-completion can be quite handy. You might want to consider having a look at the Database abstraction package from PEAR though, if you're using mysql_*somefunction* a lot, it will make life a lot easier.

---

### Post by n0ah on 2005-12-22
I'd install eclipse but it takes up so much hdd space, and when working with an 8gb hdd you keep your eye on how much space you have left..
jEdit works like a charm, and I'm loving the plugins.. so useful for what I do..

---

### Post by OneSeventeen on 2006-01-30
Okay, after viewing eclipse.org, I've learned that as stated above, it is:
> 
Eclipse is an open source community whose projects are focused on providing an extensible development platform and application frameworks for building software.

And that could be an application, a group of people, a concept, a web page, just about anything.

When trying to find out what eclipse *is* I found help files roughly 5MB and larger.

Since I'm not interested in building compiled software, I think I'll stick with stuff designed specifically for web development/PHP.

I actually bought Zend Studio 4.0, and since then, Version 5.1 has come out, and apparently upgrades were built in to the cost, which impressed me.

I know a lot of people like a lot of IDE's, but after using the Zend Development Environment, I find it takes twice as long to get the same results using Dreamweaver on my windows machine.

The only downside is dreamweaver still has the best built-in file management/transfer features, hands down.  I don't want to work remotely, and I don't want to navigate to folders just to upload files, and I also don't want to spend an extra $100 on an FTP enabled version of software (such as the next level up of Zend's development environment).

Since I'm in ubuntu, I just set up a localhost to mirror the site I'm working on, then upload everything at once, and it seems to work well.

My favorite part about Zend is the built-in PHP Documentor features, and automatic docblock generation which makes documentation a snap.  I also couldn't do without the auto-completion on not only built in PHP functions, but also all classes/methods/functions in the current project.  (not to mention variable auto-completion, which cuts down on 90% of my coding errors!)

---

