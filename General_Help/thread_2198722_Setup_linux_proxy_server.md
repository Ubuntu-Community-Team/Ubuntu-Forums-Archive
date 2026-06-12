---
title: "Setup linux proxy server"
date: 2014-01-10
forum: General Help
---

### Post by gopukrishnan on 2014-01-10
Hi,

How can I setup a proxy server which authenticate the users with Active Directory credentials. The server should do the following :
1. Block users based on specific sites.
2. Include/exclude option for specific users.
3. Authentication based on AD (Active Directory)
4. Should Provide a monthly report on the bandwidth usage for the AD users and the sites they have visited.
Any suggestions would be highly appreciated.
Squid is a great one but is it possible to do the role4 ?

Thanks,

---

### Post by TheFu on 2014-01-10
Hey back at you!  I don't know the answer to your question, sorry.

However, Linux is highly flexible since it allows building something more complex from small programs that do 1 thing well. This is a core method towards solutions.  It is common to put 5-20 of these small programs for a specific solution. Using perl or awk, you could build a report based on the log files. This is fairly standard work for an admin.  Or you could buy a commercial app that does it ... something like Splunk, I would guess.

I suspect bandwidth monitoring would need to be addressed outside the proxy ... since that is not a core function of a proxy server and with UNIX/Linux, we prefer to compartmentalize functions.

Squid can do #1 out of the box, but I block specific websites at the network layer, not at the proxy layer here. Nobody gets access from our network.
I used google to search for "squid group filter" and found this: [http://www.squidguard.org/index.html](http://www.squidguard.org/index.html)
I used google to search for "squid reporting" and found this: [http://squidanalyzer.darold.net/](http://squidanalyzer.darold.net/)
The success with these searches got me to look for "squid addons" which lead to: [http://wiki.squid-cache.org/SquidFaq/RelatedSoftware](http://wiki.squid-cache.org/SquidFaq/RelatedSoftware)

Hope these suggestions help with your research.  Sorry that I don't have any hands-on knowledge with the specific requirements.

---

### Post by SeijiSensei on 2014-01-10
I've set up a Squid proxy for a client with a lot of complex rules.  We don't use user-level authentication because people use the same workstations every day, so our access rules use IP addresses as the control.  I've written a management application in PHP that takes each night's Squid access log and imports it into a PostgreSQL database.  I then wrote a web-based interface that lets the administrators query the data in various ways.  Because Squid logs the size of each object it downloads, you could take a similar approach to bandwidth monitoring. A relatively simple script would use awk to extract the IP address of the client and the size field from the access log and dump them into a CSV file that you could import into a spreadsheet for further analysis.

Squid supports LDAP authentication, so it works with Active Directory.  Here is [one example](http://www.papercut.com/kb/Main/ConfiguringSquidProxyToAuthenticateWithActiveDirectory) and another example showing [how to write the access control rules]("https://www.linuxquestions.org/questions/linux-server-73/user-name-based-access-control-in-squid-827378/#post4138813").  This method takes advantage of Squid's built-in method to "and" ACLs by including them together in one http_access rule:
```
http_access allow permitted_sites permitted_users
http_access deny all
```
will let usernames referenced in the permitted_users ACL access sites referenced in the permitted_sites ACL and deny everyone else.

I suggest you browse the [Squid access control FAQ]("http://wiki.squid-cache.org/SquidFaq/SquidAcl").

---

### Post by gopukrishnan on 2014-01-29
Thanks all

---

