---
title: "Problem getting browser to work"
date: 2007-01-31
forum: General Help
---

### Post by petroskhan on 2007-01-31
I have only been using Ubuntu for a few weeks, and have had very few problems, and almost no complaints or issues.  Here is one of them.  

I am using Ubuntu 6.06, I have java 1.50_06 installed, and the following browsers: Firefox, Swiftfox, Epiphany, and Opera.

I trade currencies and use [www.forex.com](www.forex.com) as my platform (NOT a plug).  Currently, I am having to boot up to Windoze every time I need to access this site, which I HATE doing.

If someone could let me know if they can achieve succes, and how, I would love it!  Try this:
On the home page, click on Login in the upper right corner.  Select Practice Account (you don't need one to try this), and then Java Edition.

When I do this, another window opens, which remains blank.  I have not had any success with any of the browswers above, and am getting a little frustrated.  Ok, a lot frustrated.  

If anyone could help with this problem, he/she would become my instant Hero Of The Month...maybe the year.  Seriously, I would be most grateful, and I do apologize if this is a noob question, but I am one, so I have to deal with it.  :D

---

### Post by glabouni on 2007-01-31
Sorry, I can't help you fix this specific problem. 
what i can do is pointing you to this [guide]("I suggest you try this guide http://doc.gwos.org/index.php/VMWareXP"). Even though it won't fix your problem, it will relieve you from having to reboot into windows.

---

### Post by petroskhan on 2007-01-31
I'm getting a message that says the URL is not valid for the link you posted.  Me more confuse now.  Need more help now.  Help?

---

### Post by petroskhan on 2007-02-09
Ok, so...nobody has any ideas on this problem?  I would really like to avoid having to boot to Windows just to make use of a single website I am having trouble with.  I have even tried using Explorer in Ubuntu, which doesn't work.  I can't believe there is NO WAY to do this.  :confused:

---

### Post by llamakc on 2007-02-09
You could try running firefox from a Terminal, and as errors occur, if they are logged to the terminal's output, post that here for us.

---

### Post by llamakc on 2007-02-09
You need to install Java 1.4.2, just like the page instructs you to.

[http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

or

sudo apt-get install j2re1.4

and after it is installed use update-alternatives so your java symlink points to that version. See if that works.

---

### Post by bollix47 on 2007-02-09
According to their [_system requirements_]("http://www.forex.com/forex_support.html") it only works with windows and MAC.

You could try [_IEs4Linux_]("http://www.psychocats.net/ubuntu/ies4linux").

---

### Post by Man_Beach on 2007-02-10
Using Firefox 2.0 I get the message

'Additional plugins are required to display all the media on this page'

with an option to install the missing plugins.

I haven't tried installing the missing plugins as so far I haven't needed them for any other sites I visit - from previous posts I presume they're java related. But I certainly don't get a blank page.

---

### Post by petroskhan on 2007-02-11
I've actually tried explorer for linux, it didn't work.  I was aware that their website was designed for Mac and Windows, but I don't have a Mac, and I hate Windows.  Seems like every time I boot to Windows, I find a new virus on the computer.  I give up on Windows for everything except some games, and I'm even trying to get around that.  :D  

On the Forex website, I initially got a notice about having to install Java, which I have already done.  It gave me that notice a couple of times, now all I get is a blank page.  I am really confused about this, and would love, as I said, to completely cut the umbilical to Windows, but I really, REALLY need to use this website, and would love to find a workaround.  

Maybe it's not possible, but if anyone can find a way to make it work, I nominate him for sainthood...which may be hard, since I'm not Catholic, but I'll try.

---

### Post by bollix47 on 2007-02-12
Have you tried their [_ContactUs_]("http://www.forex.com/contact_us.html") link to determine if it's even possible to use Linux?

---

### Post by petroskhan on 2007-02-12
Hmmm...now there's an idea that actually never occured to me.  Oops?  I think I need to contact them.  Today should be good.

---

### Post by petroskhan on 2007-02-14
Well, I got a response from the website, and they're telling me to uninstall my java, then re-install it.  I am curious, since I just recently installed it.  Uninstalled, then re-installed anyway, still no go.  Getting real puzzled here.

---

### Post by WinterWeaver on 2007-02-14
I don't know if this will work, but it's worth a try.

Try installing Sun Java, all 3 options. Go to Applications >> Add/Remove, and then search for Sun Java in the search bar.

maybe that will work for you... I've tried it with Firefox (didn't install all 3) but it didn't work for me. Maybe it will work with another browser for you, once it's installed...

Good Luck anyway!

WW

---

### Post by petroskhan on 2007-02-15
I wonder if this is significant.  I did go to Apps - Add/Remove and did the search for sun java, but I only get two results for the search, both of which are already installed.  The two I have are Jave Webstart 1.4 and Sun Java 5.0 Runtime.  What is third one I am missing?  Do I need it?

---

