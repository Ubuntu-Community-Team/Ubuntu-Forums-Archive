---
title: "Are there any good rtorrent frontends?"
date: 2008-03-22
forum: General Help
---

### Post by atomkarinca on 2008-03-22
I've been trying to get *any *rtorrent frontend running since yesterday and no luck. Here are some of them I have tried and what I got:

**rtGui**

I did everything described on [its website]("http://code.google.com/p/rtgui/") but here's what I get when try to open [http://localhost/rtgui](http://localhost/rtgui)


```
Fatal error:  Call to undefined function xmlrpc_encode_request() in /opt/lampp/htdocs/rtgui/functions.php on line 197
```

Although I have xmlrpc installed, went ahead and install php5-xmlrpc too. No juice!

**wTorrent**

Followed the [website]("http://canbruixa.homelinux.net/wt/") instructions and I got it up and running BUT it cannot connect to rtorrent. It says:

	```
Error: could not connect to rtorrent
```

How does it connect to rtorrent?

**rTWi**

According to the [website]("http://projects.cyla.homeip.net/rtwi/") I've got everything right but this is what I get:

```
Warning:  parse_ini_file(/etc/rtorrent/users.conf) [[function.parse-ini-file]("http://localhost/rtwi/function.parse-ini-file")]: failed to open stream: No such file or directory in /opt/lampp/htdocs/rtwi/index.php on line 441
```

**nTorrent**

I downloaded the package from its [website]("http://code.google.com/p/ntorrent/") and according to it I just have to input one of these in a terminal:

```
./nTorrent.sh
java -jar nTorrent.jar
```

But you know what? There's no nTorrent.jar file inside that archive file. And the sh script just calls that jar file.


Sooo... Is there anyone who has got ***any*** rtorrent frontend up and running? If yes, how did you do that? What am I doing wrong? I'm going crazy here.

---

### Post by zvacet on 2008-03-22
I find [this](http://code.google.com/p/ntorrent/wiki/QuickStart) guide for ntorrent.

---

### Post by banewman on 2008-03-22
I've been using rtorrent for more than a year now and it runs great.
All I use is a maximised terminal and the rtorrent wiki -
[http://libtorrent.rakshasa.no/wiki](http://libtorrent.rakshasa.no/wiki)
With the rtorrentrc file set up like I want I have very little to do except d/load the .torrent file.
:)

---

### Post by atomkarinca on 2008-03-22
> **zvacet said:**
> I find [this]("http://code.google.com/p/ntorrent/wiki/QuickStart") guide for ntorrent.

Those are the instructions i followed but as I mentioned, there is no file called nTorrent.jar in that archive file. That's my problem.

> **banewman said:**
> I've been using rtorrent for more than a year now and it runs great.
All I use is a maximised terminal and the rtorrent wiki -
[http://libtorrent.rakshasa.no/wiki](http://libtorrent.rakshasa.no/wiki)
With the rtorrentrc file set up like I want I have very little to do except d/load the .torrent file.
:)


Thank you for the link but unfortunately I do more than just downloading torrents so I need a frontend.

---

### Post by banewman on 2008-03-22
I'm interested to know what else you do with a torrent client.
:)

---

### Post by atomkarinca on 2008-03-22
> **banewman said:**
> I'm interested to know what else you do with a torrent client.
:)


Torrent files that I download usually have more than one file in them and I select which ones to download. I need to be able to add different trackers to the torrent. And a nice GUI is never a bother for me. That's why I said I do more than *just* downloading.

---

### Post by banewman on 2008-03-22
That wiki will tell you that rtorrent does those things -
it is a fairly complete client.
:)

---

### Post by atomkarinca on 2008-03-22
> **banewman said:**
> That wiki will tell you that rtorrent does those things -
it is a fairly complete client.
:)

OK, thank you, but I want a GUI; doesn't matter if it's a web frontend.

---

### Post by banewman on 2008-03-22
From what I've just read the web gui's all need a webserver running to use them - seems peculiar.
What version of rtorrent are you running?

---

### Post by atomkarinca on 2008-03-22
> **banewman said:**
> From what I've just read the web gui's all need a webserver running to use them - seems peculiar.
What version of rtorrent are you running?

As I mentioned before; I have tried 4 different frontends, done everything described on the websites -including setting up a webserver- and I have listed the errors I got. To be more clear:

1- I know what rtorrent is, I don't want to use it through cli. I just want to run it somewhat like a daemon.

2- If you are using a frontend for rtorrent, can you please explain how you did it?

3- Also I would very much appreciate any help regarding the erros listed.

---

### Post by zvacet on 2008-03-22
I downloaded ntorrent from [here](http://code.google.com/p/ntorrent/downloads/list?q=label:Featured) and I see nTorrent.jar after I unpacked archive.

---

### Post by atomkarinca on 2008-03-22
> **zvacet said:**
> I downloaded ntorrent from [here]("http://code.google.com/p/ntorrent/downloads/list?q=label:Featured") and I see nTorrent.jar after I unpacked archive.

After some work I was, too, able to get it to run but now it gives out this error:

```
Application start failed.
Error: org.java.plugin.PluginLifeException: can't find plug-in class ntorrent.data.Environment
```

I don't know what to do with that.

---

### Post by lemonberry on 2008-03-31
> 
rtGui

I did everything described on its website but here's what I get when try to open [http://localhost/rtgui](http://localhost/rtgui)

Code:

Fatal error:  Call to undefined function xmlrpc_encode_request() in /opt/lampp/htdocs/rtgui/functions.php on line 197

Although I have xmlrpc installed, went ahead and install php5-xmlrpc too. No juice!


The error message is produced when you don't have the XMLRPC library for PHP5 installed.  This is not an rtGui issue - more your local configuration.   You did not "do everything described on it's website"....

---

### Post by Thyferran on 2008-04-01
I had this error after installing rtGUI and it was simply because I had forgotten to restart Apache after installing php5-xmlrpc

A simple 

```
sudo /etc/init.d/apache2 restart
```

Should fix it.

---

