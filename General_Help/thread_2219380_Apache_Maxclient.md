---
title: "Apache Maxclient"
date: 2014-04-23
forum: General Help
---

### Post by Ri_CatB_Support on 2014-04-23
Hi,

I want to check the concurrent users who established the connection to apache, 

I tried with the below command to check the concurrent users:

netstat -plan | grep :80 | wc -l

Can anyone please confirm if i'm right or is there any other way to check concurrent users.


Purpose: I want to write script to check the Apache maxclient users,  so if it reaches the maximum i will trigger a alert.

Thanks in advance!

Regards,
Prakash

---

### Post by SeijiSensei on 2014-04-23
Unless people are downloading large files, most connections to a web server are so transitory that you would rarely max out the number of concurrent connections.  I've run Apache for years, and I don't think I've ever hit the limit.  I'm using prefork MPM with these settings:
```

<IfModule prefork.c>
StartServers       5
MinSpareServers    5
MaxSpareServers   10
ServerLimit      256
MaxClients       256
MaxRequestsPerChild  4000
</IfModule>

```
At the moment I have about a dozen children listening.

---

### Post by Ri_CatB_Support on 2014-04-25
Hi [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195"),

Thanks for your response,

Can you please let me know if i want to increase this server limit and max client value, do i need to increase the RAM size, and other server related configuration?

and also can you please let me know the command to check the concurrent users currently whoever logged in to the site.

Thanks in advance!

---

### Post by SeijiSensei on 2014-04-25
Concurrent users?  I don't know if there is any command for that.  Look at /var/log/apache2/access.log, and you'll see all the requests with timestamps.  Unless you have lots of connections with nearly identical timestamps and different IP addresses or hostnames, there are no concurrent users.

I sincerely doubt that changing the defaults will markedly improve performance.  What kind of traffic is this machine handling?  If it's just ordinary web pages, you'll probably never hit any limits.  If you have dozens of people download multi-megabyte files simultaneously, you may need to do some tweaking.  Unless you describe the nature of the traffic the server is handling, it's hard to diagnose performance.

Has anyone complained that the server seems slow, or that they cannot get a connection?  If not, I doubt you need to change anything.  If you're concerned, I'd start by reading [http://httpd.apache.org/docs/2.2/misc/perf-tuning.html](http://httpd.apache.org/docs/2.2/misc/perf-tuning.html).

---

### Post by Ri_CatB_Support on 2014-04-26
Hi S[COLOR=#000000]eijiSensei,

/var/log/apache2/access.log   -  This will be helpful for me, 

Actually our machine handling the application requests where many numbers users are logging externally(worlwide), Normally during the production hours users will be high, at once we faced the issue, website was went down due to maximum number of users hit the limits. Hence we are trying to put some alerts before it reaches the maximum.

Hence im looking exactly to capture concurrent users from Ubuntu where application is hosted.

I tried googling and got the below command, when i tried using this command i was getting some count, but not sure whether this is right or not.

netstat -plan | grep :80 | wc -l

I appreciate your help!

Regards,
Prakash
[/COLOR]

---

### Post by SeijiSensei on 2014-04-26
> I tried googling and got the below command, when i tried using this command i was getting some count, but not sure whether this is right or not.

netstat -plan | grep :80 | wc -l

That seems to return the number of simultaneous active listeners at a specific point in time, so yes, it does return one of the pieces of information you're interested in.  The only problem I see is how transitory the connections are.  If I run that command repeated on my server I seem to get either one or a number between 19 and 35.  If you leave off the "| wc -l" which generates the counts, you'll see records like this:
```
tcp        0      0 ::ffff:my.server.ip.addr:80     ::ffff:68.60.56.33:59549    TIME_WAIT   -                   
tcp        0      0 ::ffff:my.server.ip.addr:80     ::ffff:175.142.78.2:50518   TIME_WAIT   - 

```
68.60.56.33 has about a dozen simultaneous requests, no doubt for the images on the site as well as the page content.

You could wrap that command in a script to run repeatedly with a "sleep 1" pause in each loop and report the count by timestamp.

Do you run a log analyzer like webalizer or analog?  I'd definitely set up one of them to summarize your access.log.  You'll be able to see how often each URL is hit and which remote clients generate most of the traffic.  That will help you get a general sense about traffic.

You can also do things like grepping access.log for specific requests and counting up the number of accesses by remote IP.  Here's a quick-and-dirty approach:
```

#!/bin/bash

LOG=/var/log/apache2/access.log
# look for request for the main index page
FIND_URL="/"

# compile list of unique requesting IP addresses
REMOTES=$( grep "GET $FIND_URL" < $LOG | awk '{print $1}' | sort | uniq )

for addr in $REMOTES
do
    # identify remote
    HOST=$(host $addr | awk '{print $5}')
    # count up requests for each remote host
    echo "$HOST [$addr]: $(grep $addr $LOG | wc -l)"  
done

exit 0

```

You'll get results that look like this:
```

3(NXDOMAIN) [12.197.12.226]: 6
baiduspider-123-125-71-100.crawl.baidu.com. [123.125.71.100]: 1
baiduspider-123-125-71-12.crawl.baidu.com. [123.125.71.12]: 2
baiduspider-123-125-71-13.crawl.baidu.com. [123.125.71.13]: 6
baiduspider-123-125-71-14.crawl.baidu.com. [123.125.71.14]: 10
baiduspider-123-125-71-15.crawl.baidu.com. [123.125.71.15]: 7

```
You can play with the script and change how the filters are done.  For instance, maybe you would want to filter by time of day.

The log analyzers are a better approach though, unless you have specific things you're looking for.  Here's a [sample analog report]("http://www.chiark.greenend.org.uk/~sret1/stats/").  Both analog and webalizer are in the repositories.

---

### Post by Ri_CatB_Support on 2014-05-04
Thanks for your kind help..

It gave me more useful information.

Once again thanks for your help...

Regards,
Prakash

---

### Post by Ri_CatB_Support on 2014-05-12
Hi,

We have written a script to check apache max client and it is working fine.

Now we have observed that, during peak hours(i.e business hours) suddenly we are receiving max client value threshold reached 350, or 370 etc..

Actual value set for max client is 150, then how come these values are breaching.. then it turn tends to down the application.

After restarting the application, maxclient value returned back to normal. So my concern is how this values are increasing heavily eventhough maxclient value set to 150.

Your help is highly appreciated.

Please let me know if you need any more information.

Regards,
Prakash

---

