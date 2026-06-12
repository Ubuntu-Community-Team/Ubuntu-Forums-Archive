---
title: "HTML file viewing options?"
date: 2020-04-14
forum: General Help
---

### Post by c_xy on 2020-04-14
Hello, I'm running 18.04 LTS server.

Is there a way to view .html files offline? A viewer app?

We want to prevent users from browsing other sites over the internet. However, we have files on our server that are html files we need to view.

One possible alternative is to restrict the a web browser like Firefox to only view local files,i.e. "file:///"

Any help would be appreciated. 

Thanks.

c_xy

---

### Post by TheFu on 2020-04-14
Don't route traffic to the internet.  Anything less will fail.  There are all sorts of problems trying to have a modern browser view local files. They don't want that, but you can have them access an internal web-server.

lynx, dillo, are options, but you can use the bigger, bloated browsers too. They just don't like the file://// urls anymore.  Special settings will be require.  
**$ chromium-browser --allow-file-access-from-files**
Firefox doesn't have a CLi option, so a new profile will be needed.

---

### Post by c_xy on 2020-04-14
Thanks for your reply TheFu. Sounds like my options are limited.

We would have to route traffic through the internet for updates, etc.

We don't really use firefox at all. That is just the default browser. We removed it, since we don't browse the web on our server. The issue is that for some of the applications we run our server, summary reports are generated in html format. The only way to view them on the server is through a browser? PDF file have different application viewers. How about html files? Does such a thing exist without accessing the internet? 

1. Can we restrict firefox to only view local files, i.e., files:///
2. Is there a command line option to convert html to pdf files,  so we can read them with a pdf viewing application?

Thanks

c_xy

---

### Post by TheFu on 2020-04-14
You really need to do what schools do to prevent outside content access. 

Patching doesn't actually require internet access.  Setup an APT-cache system.
Only the internet proxy server needs access to the internet.  Disable the proxy unless you are actively patching.

Or just have a WAN firewall rule for the LAN where desktop systems sit that prevent external access.

There are many ways to create PDF files.  htmltopdf, or use something like nextcloud or wallabag to store the files.  Anyone who converts HTML to PDF should be shot, in my book.  PDF should only be used when page layout must be maintained.  For any other reason, stay with the most flexible format possible.  Simple HTML is probably the most efficient, attractive encoding possible.

For a business, you really should engage a professional to work through the entire use-case and have strategies for each situation.

---

### Post by SeijiSensei on 2020-04-14
1) Set up a Linux machine running Apache or nginx.

2) Move your files to that server.

3) On your firewall block outbound traffic to remote ports 80 and 443.

---

### Post by TheFu on 2020-04-14
> **SeijiSensei said:**
> 1) Set up a Linux machine running Apache or nginx.

2) Move your files to that server.

3) On your firewall block outbound traffic to remote ports 80 and 443.

Definitely agree with that part for the documents. Stated much more clearly than I did.

I haven't checked whether apt-cacher-ng prevents each client from needing access to the internet or not.  That would be my next step. Checking whether the package management caching tool caches "update" actions too.  What does this mean for snaps as those become more common?

```
$ cd /var/cache
$ sudo du -sh apt-cacher-ng
2.1G    apt-cacher-ng
```

That's pretty small for the 15 systems here. I'm only using it for 16.04 production systems.  Haven't bothered forcing any newer, test, systems to use the apt-cacher.

Don't forget to block external DNS access for every desktop.  People can setup tunnels over DNS requests if they want. It is a common exfill tactic. [https://blogs.akamai.com/2017/09/introduction-to-dns-data-exfiltration.html](https://blogs.akamai.com/2017/09/introduction-to-dns-data-exfiltration.html)  Probably need to leave it at that here to stay inside forum rules.

* Block desktops from all WAN/Internet access at the WAN firewall. All ports, not just popular web, email, DNS.
* Check that system patching is still possible or mitigate that aspect, somehow.
* Check that non-traditional package management is blocked as you require.
* Run trials for a few weeks on selected desktop systems in each department to see what access may still be needed.

If this is for a bank, financial service, or health delivery company, engage a team to ensure those laws are followed and you don't get *early retirement* if a mistake happens.

If the local users **do not** have sudo/root on their workstations, then some local prevention could be used, but I wouldn't trust it unless all external ports are locked or disabled with hot-glue.  If anyone can insert a flash drive or SDcard or any other sort of device, then they can bypass all local controls. As always, physical access is king.

---

### Post by pqwoerituytrueiwoq on 2020-04-15
if you do not want a web browser installed and you only need to view reports you could use wkhtmltopdf to convert the html files to pdf files

there is this thing called proxy settings in web browsers, you could config that to something that does not work easy to bypass but it is also easy to put a browser install on a flash drive

---

### Post by SeijiSensei on 2020-04-16
> * Block desktops from all WAN/Internet access at the WAN firewall. All ports, not just popular web, email, DNS.

I interpreted his request as meaning he wanted to allow certain types of Internet access just not HTTP/HTTPS requests.  Otherwise, a rule that blocks all outbound traffic at the firewall is obviously the best choice.

---

### Post by c_xy on 2020-04-28
Thank you everyone for your suggestions. Really helpfu. A lot to ponder.

For now, we'll probably use the wkhtmltopdf suggestion. It is suffice for our purposes since we do not access web browsers other than to infrequently view html files. Down the road, we may further explore the other helpful suggestions in this thread.

Thanks to all.

c_xy

[COLOR=#000000]


[/COLOR]

---

