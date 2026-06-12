---
title: "Squidguard ERROR: Going into emergency mode"
date: 2016-01-29
forum: General Help
---

### Post by jlee3 on 2016-01-29
Greetings,

I'm a newb when it comes to Linux and I've been trying to setup squid and squidguard for a few days so that I can blacklist sites for my kids. I think I'm getting close to finishing the configuration, but I'm getting the following error message: ERROR: Going into emergency mode when I look at the squidguard log file located in /var/log

Here's the log:
```

2016-01-29 13:52:11 [5916] INFO: New setting: dbhome: /var/lib/squidguard/db/blacklists
2016-01-29 13:52:11 [5916] INFO: New setting: logdir: /var/log/squidguard
2016-01-29 13:52:11 [5916] Added User: jlee
2016-01-29 13:52:11 [5916] init domainlist /var/lib/squidguard/db/blacklists/ads/domains
2016-01-29 13:52:11 [5916] INFO: create new dbfile /var/lib/squidguard/db/blacklists/ads/domains.db
2016-01-29 13:52:11 [5916] init urllist /var/lib/squidguard/db/blacklists/ads/urls
2016-01-29 13:52:11 [5916] INFO: create new dbfile /var/lib/squidguard/db/blacklists/ads/urls.db
2016-01-29 13:52:11 [5916] init expressionlist /var/lib/squidguard/db/blacklists/ads/expressions
2016-01-29 13:52:11 [5916] init domainlist /var/lib/squidguard/db/blacklists/spyware/domains
2016-01-29 13:52:11 [5916] INFO: create new dbfile /var/lib/squidguard/db/blacklists/spyware/domains.db
2016-01-29 13:52:12 [5916] init domainlist /var/lib/squidguard/db/blacklists/porn/domains
2016-01-29 13:52:16 [5916] INFO: create new dbfile /var/lib/squidguard/db/blacklists/porn/domains.db
2016-01-29 13:52:17 [5916] init urllist /var/lib/squidguard/db/blacklists/porn/urls
2016-01-29 13:52:18 [5916] INFO: create new dbfile /var/lib/squidguard/db/blacklists/porn/urls.db
2016-01-29 13:52:18 [5916] init expressionlist /var/lib/squidguard/db/blacklists/porn/expressions
2016-01-29 13:52:18 [5916] squidGuard: destination porn is defined in configfile /etc/squidguard/squidGuard.conf
2016-01-29 13:52:18 [5916] ERROR: Going into emergency mode

```
This is my squidguard config file:
```

#
# CONFIG FILE FOR SQUIDGUARD
#
# Caution: do NOT use comments inside { }
#


dbhome /var/lib/squidguard/db/blacklists
logdir /var/log/squidguard


#
# TIME RULES:
# abbrev for weekdays: 
# s = sun, m = mon, t =tue, w = wed, h = thu, f = fri, a = sat


time workhours {
	weekly smtwhfs 08:00 - 19:30
	date *-*-01  08:00 - 19:30
}


#
# SOURCE ADDRESSES:
#


src admin {
	ip  		10.1.1.0/24
	user		jlee
	within		workhours
}


src clients {
	ip		10.1.1.0/24
}




#
# DESTINATION CLASSES:
#
# [see also in file dest-snippet.txt]


dest ads {
	domainlist	ads/domains
	urllist		ads/urls
	expressionlist	ads/expressions
	redirect [http://cnn.com](http://cnn.com)
}


dest spyware {
	domainlist	spyware/domains
	redirect [http://cnn.com](http://cnn.com)
}


dest porn {
	domainlist	porn/domains
	urllist		porn/urls
	expressionlist	porn/expressions
	redirect [http://cnn.com](http://cnn.com)
}


#dest adult {
#	domainlist	BL/adult/domains
#	urllist		BL/adult/urls
#	expressionlist	BL/adult/expressions
#	redirect [http://admin.foo.bar.de/cgi-bin/blocked.cgi?clientaddr=%a&clientname=%n&clientuser=%i&clientgroup=%s&targetgroup=%t&url=%u](http://admin.foo.bar.de/cgi-bin/blocked.cgi?clientaddr=%a&clientname=%n&clientuser=%i&clientgroup=%s&targetgroup=%t&url=%u)
#}


#
# ACL RULES:
#


dest porn {
	domainlist porn/domains
	urllist porn/urls
	}
acl {
	admin {
		pass	 any
	}


	clients within workhours {
		pass	 good !ads !spyware !porn any
	} else {
		pass any
	}


		default {
		pass	good !ads !spyware !porn any 
		redirect [http://cnn.com](http://cnn.com)
	}
}

```

Any help would be greatly appreciated.

---

### Post by Melnik_Hoogland on 2016-01-29
I haven't used squidguard before, but is there a reason why
```
dest porn
```
is defined twice? It looks like the second time it's defined it doesn't do anything that isn't done by the first definition, so I'd try removing the second definition and trying again.

---

### Post by jlee3 on 2016-01-29
Squidguard is what you can use to blacklist websites. Proxy only allows or denies access to the internet. Also, it's to block my kids from going to those sites.

So now I edited the squidGuard.conf file with the following and it's not giving me that error anymore but for some reason it's not blocking the sites in the database. Thanks for the help. Also, I've added this line in the squid3/squid.conf file: url_rewrite_program /usr/bin/squidGuard -c /etc/squidguard/squidGuard.conf

```
#
# CONFIG FILE FOR SQUIDGUARD
#
# Caution: do NOT use comments inside { }
#


dbhome /var/lib/squidguard/db/blacklists
logdir /var/log/squidguard


#
# TIME RULES:
# abbrev for weekdays: 
# s = sun, m = mon, t =tue, w = wed, h = thu, f = fri, a = sat


#time workhours {
#    weekly smtwhfs 08:00 - 19:30
#    date *-*-01  08:00 - 19:30
#}


#
# SOURCE ADDRESSES:
#


# src admin {
#    ip          10.1.1.0/24
#    user        jlee
#    within        workhours
#}


#src Home_network {
#    ip        10.1.1.0/24
#    within        workhours
#}




#
# DESTINATION CLASSES:
#
# [see also in file dest-snippet.txt]


dest ads {
    domainlist    ads/domains
    urllist        ads/urls
    expressionlist    ads/expressions
    redirect [http://google.com](http://google.com)
}


dest spyware {
    domainlist    spyware/domains
    redirect [http://google.com](http://google.com)
}


dest porn {
    domainlist    porn/domains
    urllist        porn/urls
    expressionlist    porn/expressions
    redirect [http://google.com](http://google.com)
}


#dest adult {
#    domainlist    BL/adult/domains
#    urllist        BL/adult/urls
#    expressionlist    BL/adult/expressions
#    redirect [http://admin.foo.bar.de/cgi-bin/blocked.cgi?clientaddr=%a&clientname=%n&clientuser=%i&clientgroup=%s&targetgroup=%t&url=%u](http://admin.foo.bar.de/cgi-bin/blocked.cgi?clientaddr=%a&clientname=%n&clientuser=%i&clientgroup=%s&targetgroup=%t&url=%u)
#}


#
# ACL RULES:
#


#dest porn {
#    domainlist porn/domains
#    urllist porn/urls
#    expressionlist    porn/expressions
#    }
acl {
#    admin {
#        pass     any
#    }
#
#    Home_network within workhours {
#        pass     !ads !spyware !porn all
#    } else {
#        pass any
#    }


        default {
        pass    !ads !spyware !porn any 
        redirect [http://google.com](http://google.com)
    }
}
```

---

### Post by Melnik_Hoogland on 2016-01-30
Is there a reason you used "any" instead of "all" in the default section? I don't see it anywhere in the documentation, so I'd try replacing it with "all". Also, I don't see "redirect" used in any of the sample destination definitions, so I'd try removing that if it still doesn't work.

---

