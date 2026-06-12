---
title: "Automatically watching Web sites for changes"
date: 2013-10-16
forum: General Help
---

### Post by davidtuti2 on 2013-10-16
Hi,

I would like to know if there exits some application (command line if is possible) to can automatically detect Web sites for changes.

Many thanks and sorry for my english!

---

### Post by tgalati4 on 2013-10-16
Perhaps a script that scrapes the web page once every 2 hours then compares the two:

```
man curl
man diff
```

I don't know of an automated solution.  I'm sure there are paid services that do something similar.

---

### Post by TheFu on 2013-10-16
Many websites support RSS - only if there are new articles would the RSS show a change. Lots of RSS readers exist - any you can certainly use wget, curl, lynx, to pull RSS feeds if you need an automatic way to monitor a website.  If it is a blog or 500 blogs you are trying to monitor, there are spiders that do this .... 

I'd also point out that grabbing the same website every 5 minutes would be considered abuse by many, especially the smaller, personal sites.  When I see that sort of abuse, I'll block the user agent or subnet.  I just don&#8217;t have the bandwidth to waste on that crap, especially since my tiny blog gets updated about once a week.  No "breaking news" happens on it. Checking once a day would be enough.

With RSS, there is often a timestamp that can be checked for the last time anything changed. If it isn't different, no need to look any further.  Pulling the entire webpage local and using diff can work, unless the site has ads. those will change all the time, so you'd need to be smart.

---

### Post by Lars Noodén on 2013-10-16
RSS works well.  So do similar feeds like atom, if they are available. If they are not available, you might prompt the site's webmaster to look into setting up such a feed.  It will save them bandwidth if there are a lot of people trying to follow the site.  

If you are stuck without RSS or atom, then you can try to put something together with curl, wget or a script of your own.  It's not too hard to put together your own web client using CPAN's LWP in perl, which should be already installed by default on your system.  See "man LWP" and the list of other modules at the bottom of the man page.  

Either way, you'll want to probe using just the HEAD method and could consider sending the [if-modified-since](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.25) header to prevent unnecessary transfer of unchanged pages.

---

### Post by SeijiSensei on 2013-10-16
Curl has a -z parameter that lets you specify either a local file or a timestamp.  It then will only update files newer than the local copy or the timestamp.  From the curl [manual](http://curl.haxx.se/docs/manual.html),

```

 For example, you can easily make a download that only gets performed if the
 remote file is newer than a local copy. It would be made like:
 
        curl -z local.html http://remote.server.com/remote.html
 
 Or you can download a file only if the local file is newer than the remote
 one. Do this by prepending the date string with a '-', as in:
 
        curl -z -local.html http://remote.server.com/remote.html
 
 You can specify a "free text" date as condition. Tell curl to only download
 the file if it was updated since January 12, 2012:
 
        curl -z "Jan 12 2012" http://remote.server.com/remote.html
 
 Curl will then accept a wide range of date formats. You always make the date
 check the other way around by prepending it with a dash '-'.

```

One of these methods should work when incorporated into an appropriate bash script.

---

### Post by Lars Noodén on 2013-10-16
wget is about the same to implement.

```

wget -q --timestamping http://xx.yy.zz.aa/test.html

```

Though curl is less than half the size of wget, so it is quite likely more efficient.

---

### Post by davidtuti2 on 2013-10-18
Hi,
Many thanks for all your answers.
Well the website don't have RSS. I can't contact with the administrator.
would be possible to create my own RSS from these website?
Many thanks and sorry for my english!

---

### Post by Lars Noodén on 2013-10-18
If you look around there should be an About page or some other page with contact information for someone in charge of the site.  That would be the best way.  Only the webmaster can set up an RSS or atom feed for a site.  

Outside of that, you could set up a cron job to run every hour or two and check the site.  wget is already on your machine.

```

#!/bin/sh

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

url=http://www.ipl.org/;

file1=xxxx1.html;
file2=xxxx2.html;
dir=/tmp/web;

test -d $dir || mkdir -p $dir;
test -f $dir/$file1 || touch $dir/$file1;
test -f $dir/$file2 || touch $dir/$file2;

wget -q --timestamping -O $dir/$file1 $url;

if ! diff -q $dir/$file1 $dir/$file2 > /dev/null; then
  # echo DIFFERENT;
  cp -p $dir/$file1 $dir/$file2;
  DISPLAY=:0.0 exec firefox $url;
fi

```

There used to be a trick to make Firefox open the URI in a specific tab or window, but that seems to have changed or been removed.

---

### Post by TheFu on 2013-10-18
> **davidtuti2 said:**
> Hi,
Many thanks for all your answers.
Well the website don't have RSS. I can't contact with the administrator.
would be possible to create my own RSS from these website?
Many thanks and sorry for my english!

It is always possible to contact almost every website admin, unless they are doing something illegal. The contact data is public - use domain registrar data or send and email to webmaster, postmaster or root @domain.com. Someone should be monitoring at least one of those addresses.  I've contacted newspapers and gotten them to add RSS feeds before.  A few websites might hide that data, so you just contact the network provider.  If you send a registered letter, they should get it.

If you are planning to do something against their ToS or illegal, don't expect much help.  Scroogle was taken down that way. Any website can make it difficult for anyone to visit, if they want. I know that I do for hogs .... like Baidu who NEVER send any referrals, but were eating 80% of my bandwidth. Why would I allow that?

Would it be possible to create your own RSS?  Probably with a little scripting. Any of the popular scripting languages could certainly do it. Be as complex and "good" as you like. Good enough might be just a few lines, as outlined above.

I'm positive that your English is better than my ... well, whatever language you natively speak. If I wasn't fairly certain of correct understanding, I would have asked for clarity.

---

