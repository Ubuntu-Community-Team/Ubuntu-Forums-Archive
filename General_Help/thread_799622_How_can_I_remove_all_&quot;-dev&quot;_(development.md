---
title: "How can I remove all &quot;-dev&quot; (development header) packages, except mandatory ones?"
date: 2008-05-19
forum: General Help
---

### Post by allanlewis on 2008-05-19
Hi,

I've been using Ubuntu since Dapper and I've had an irritating problem regarding compiling programs from source. I occasionally do this when a package of the latest version isn't available, although I generally limit myself to simple programs - [Lyx]("http://www.lyx.org/") is the most complex thing I've compiled myself so far.

As anyone who's ever compiled anything from source knows, several development header packages, typically with names ending "-dev", need to be installed to compile anything but the simplest of programs. However, some of these take up quite a lot of space (a recent program needed about 40MB of headers) and I like to remove them if I'm not planning on compiling anything else in the near future. (My internet connection is reasonably fast, so downloading them again isn't a major issue.) However, I can't just search Synaptic for "-dev" and remove all the installed packages in the list because some of them are mandatory; i.e. "ubuntu-desktop" or "kubuntu-desktop" depend on them. (I am using Kubuntu Gutsy at the moment - planning to upgrade to Hardy soon - but I prefer Synaptic to Adept Manager.) So I have to go down the list and remove each on in turn, checking it isn't a dependency of anything important.

I have had a few guesses at a solution to this, e.g. removing all the "-dev" packages and installing "(k)ubuntu-desktop" in one step, but I don't know how to do this and I don't want to mess up my system. I also notice that apt keeps a list of packages it can automatically remove, but I often notice packages I purposely installed on there, so I don't just want to do "apt-get autoremove" in case I remove something I need.

Can anyone help me?

Allan Lewis.

---

### Post by cdtech on 2008-05-19
I know you can clean out the local repository of retrieved package files using apt-get clean. I probably have this wrote down somewhere, I'll have a look see.......

---

### Post by latna on 2008-05-19
Well no matter what you're probably in for some tedious work, but maybe this will get you started. Run this in a terminal to get a list of packages that have the word "dev" in them.

```
dpkg -l *dev* | gawk '{print $2}' 
```

Then you can use apt-cache to see if anything depends on that package.

```
apt-cache rdepends PACKAGE_NAME
```

Then you can decide if you want to remove it.

Good luck.

---

### Post by latna on 2008-05-19
> **latna said:**
> Then you can use apt-cache to see if anything depends on that package.

```
apt-cache rdepends PACKAGE_NAME
```


Sorry. I did some experimenting and founds out that command will print out all packages that depend on PACKAGE_NAME whether they're installed or not.

It could still be useful I guess. But it won't help you clean out everything. Not easily anyway.

---

### Post by allanlewis on 2008-05-19
> **cdtech said:**
> I know you can clean out the local repository of retrieved package files using apt-get clean. I probably have this wrote down somewhere, I'll have a look see.......

I know about that command but it doesn't do what I want.

> **latna said:**
> Well no matter what you're probably in for some tedious work, but maybe this will get you started. Run this in a terminal to get a list of packages that have the word "dev" in them.

```
dpkg -l *dev* | gawk '{print $2}' 
```

Then you can use apt-cache to see if anything depends on that package.

```
apt-cache rdepends PACKAGE_NAME
```

Then you can decide if you want to remove it.

Good luck.

That's basically what I do with Synaptic, but in a more techie way :D

> **latna said:**
> Sorry. I did some experimenting and founds out that command will print out all packages that depend on PACKAGE_NAME whether they're installed or not.

It could still be useful I guess. But it won't help you clean out everything. Not easily anyway.

As you say, that command isn't helpful either. I really want a command that does:
[INDENT]*remove all packages with names containing "-dev" that do not require the removal of <list of packages>*[/INDENT]
(<list of packages> would basically just be "ubuntu-desktop" or "kubuntu-desktop", as appropriate)
However, I wouldn't be keen on trying to do this entirely automatically as I could end up doing something stupid like removing every package from my system!

---

