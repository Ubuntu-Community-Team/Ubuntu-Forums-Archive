---
title: "Looking for an open source order inventory solution"
date: 2017-05-27
forum: General Help
---

### Post by daryl9 on 2017-05-27
Hello,

I have a small NGO, meaning, my wife and myself as the primary operations personnel.  This foundation donates computer equipment to underprivileged schools in the Philippines.  

I have a stock of computer systems, companies donating that equipment, schools applying for donations and systems in various stages of being built, or being prepared for shipment.  All of this is getting challenging for me to maintain and keep organized.

I've been looking for an open source inventory/order management solution.  This solution has to be affordable, meaning free, or very, very cheap.  The systems that I donate to the schools use Edubuntu, the educational version of Ubuntu, so I prefer to have this solution run on Ubuntu.  

The majority of the solutions that I've found claim to be open source, they may have been built on open source tools, but for me to use it, I have to pay a subscription, and that isn't going to work. My foundation can't afford it, plus, I don't have the internet connectivity for a cloud based solution.  Other solutions that I've found, that are truly open source, are just not up to the task.  Not ready for prime time, very difficult to figure out, very poor documentation, or just don't work.

I am looking for suggestions, or idea's if someone knows of a something that will run on Ubuntu, preferably, plug-n-play, without a lot of development work involved, please let me know.

Daryl

---

### Post by oldfred on 2017-05-27
While not directly for inventory, these are for recording data.

 Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/) 

I think in searching have found various python, database applications that you can download from git or a web site.
If you know or are willing to learn python then you can modify to suit.

Bit more advanced, starting from scratch.
[https://pythonspot.com/en/python-database-programming-sqlite-tutorial/](https://pythonspot.com/en/python-database-programming-sqlite-tutorial/)

One of first found in google search. No idea if useful or not.
[http://www.gidnetwork.com/b-123.html](http://www.gidnetwork.com/b-123.html)

---

### Post by daryl9 on 2017-05-27
> **oldfred said:**
> While not directly for inventory, these are for recording data.

 Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/) 

I think in searching have found various python, database applications that you can download from git or a web site.
If you know or are willing to learn python then you can modify to suit.

Bit more advanced, starting from scratch.
[https://pythonspot.com/en/python-database-programming-sqlite-tutorial/](https://pythonspot.com/en/python-database-programming-sqlite-tutorial/)

One of first found in google search. No idea if useful or not.
[http://www.gidnetwork.com/b-123.html](http://www.gidnetwork.com/b-123.html)

I'm not a developer, and I really don't want to try to code something.  I've considered standing up a Lamp type environment on a machine, and writing something in php/mysql/apache, but it would take me to long, and just be to challenging for me.  I'm a systems guy, an OS guy, I prefer leaving the development up to others who enjoy it.  :)

Thank you for the reply.

Daryl

---

### Post by mörgæs on 2017-05-27
Have you played with Google Docs and Google Forms?

---

### Post by dragonfly41 on 2017-05-27
Since you have considered building on a LAMP environment there are frameworks which offer ready to use demos.

Here is one .. [http://www.jqwidgets.com/jquery-widgets-demo/showcasedemos/](http://www.jqwidgets.com/jquery-widgets-demo/showcasedemos/)

Not too much development work since you can adapt the demos.

You can use this under the non commercial licence.

And if you want to avoid cloud LAMP servers you could make your own localhost LAMP server available using [https://ngrok.com](https://ngrok.com). 
But make sure it is secured with SSL etc.

---

### Post by daryl9 on 2017-05-27
> **mörgæs said:**
> Have you played with Google Docs and Google Forms?

Google dos/forms would require internet access, which I do not have in my location.  This has to be a stand alone environment. 

Thank you for the suggestion.

Daryl

---

### Post by daryl9 on 2017-05-27
> **dragonfly41 said:**
> Since you have considered building on a LAMP environment there are frameworks which offer ready to use demos.

Here is one .. [http://www.jqwidgets.com/jquery-widgets-demo/showcasedemos/](http://www.jqwidgets.com/jquery-widgets-demo/showcasedemos/)

Not too much development work since you can adapt the demos.

You can use this under the non commercial licence.

And if you want to avoid cloud LAMP servers you could make your own localhost LAMP server available using [https://ngrok.com](https://ngrok.com). 
But make sure it is secured with SSL etc.

I am very comfortable with using a LAMP solution.  I had considered doing a LAMP solution, with MySQL, PHP Apache, but it would be to challenging for me.

I'll take a look at the jgwidgets and see what it can do for me.

Thank you for the suggestion.

Daryl

---

### Post by dragonfly41 on 2017-05-27
Some added notes.

If you focus on this page ...

[http://www.jqwidgets.com/jquery-widgets-demo/demos/php/index.htm#demos/php/listbox.htm](http://www.jqwidgets.com/jquery-widgets-demo/demos/php/index.htm#demos/php/listbox.htm)

there are three areas ...

[1] Web UI Widgets

[2] PHP Integration

[3] Demo | View Source (at bottom of the page).

...


Hide the web UI Widgets area for now.
Now if you click on any of the PHP Integration demos you see each demo rendered at the bottom of the page.
You can click on "View Source" to copy the working code into your own LAMP setup.

An editor like Adobe Brackets is useful too.

[https://askubuntu.com/questions/762855/how-to-install-brackets-io-from-the-command-line](https://askubuntu.com/questions/762855/how-to-install-brackets-io-from-the-command-line)

---

