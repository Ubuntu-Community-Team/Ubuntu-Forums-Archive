---
title: "Adding a TXT Record to Ubuntu 16.04 LTS"
date: 2018-07-06
forum: General Help
---

### Post by fatzmccracken on 2018-07-06
I have been asked to add a TXT record to my company's internal Public DNS servers. I inherited these two servers from the previous sysadmin and have almost no familiarity with the Ubuntu CLI env. In fact, the few common commands like "list" or "ls" don't even work on these servers.

 Can someone provide me step-by-step instructions to add a TXT record to Ubuntu's DNS? 

 Almost everything I find on the web relates to making these changes to various Public DNS GUIs - not to the Ubuntu CLI.

 I will need very step-by-step instructions in consideration of my lack of Ubuntu CLI skills, or.....a link to a How To article\video that I may have missed would be appreciated.

To be specific - the purpose is to add a verification for a Cloud Service. So I have the text string to add, just no idea How.

Thanks!

---

### Post by SeijiSensei on 2018-07-06
Let me ask a few questions to begin.

First, are the hosts in your local network collected into a domain like mycompany.com or mycompany.local?  The records for a domain are stored in what's called a "[zone file]("https://help.ubuntu.com/community/BIND9ServerHowto#Zone_File")."  On Ubuntu, it should be stored in the directory /etc/bind.  The zone file maps hostnames to IP addresses and specifies basic information about a domain like the location of its DNS nameservers (NS records) and the names of any mail servers (MX records). 

A TXT record is like those NS and MX records.  It usually appears in the global section of a zone file.  For instance, here's the top of a sample zone file for a domain I manage, with identifying material scrubbed:

```

example.com             IN SOA  example.com. admin.example.com. (
                                2018070301 ; serial
                                432000      ; refresh (5 days)
                                3600       ; retry (1 hour)
                                86400      ; expire (1 day)
                                3600       ; minimum (1 hour)
                                )

                IN      NS      ns.example.com.
                IN      NS      ns2.example.com.

                IN      MX      0 mail.example.com.
                IN      MX      10 mail2.example.com.

                IN      TXT     "v=spf1 a:mail.example.com a:mail2.example.com ~all"

etc.

```

This provides the "Statement of Authority" (SOA) record for the hypothetical domain example.com.  The NS and MX records define the locations of the name and mail servers for the domain.  That's followed by a TXT record that I use to comply with the "[Sender Policy Framework]("http://www.openspf.org/Introduction")" (SPF) used for email.  You would place your TXT file there.

As for editing the file, see if you have a file named something like /etc/bind/db.example.com.  If so, type the command "sudo nano /etc/bind/db.example.com" to edit the file.  Nano has a built-in command menu at the bottom of the screen.  All the commands require holding down the Ctrl button, represented in the menu as "^", and typing a letter.  For instance, Ctrl+W ("Write") saves the current file.

If there is no /etc/bind/db.example.com, try the following

```

cd /etc/bind
grep file *

```

That will find all lines containing the word "file" in all the files in /etc/bind.  One of them should be a line that defines the location of the zone file for your local domain.  That's the one you'll need to edit.

---

### Post by fatzmccracken on 2018-07-06
Ok, I'm learning and I think I'm almost there - we do have a registered domain, so we can use "example.com" as our theoretical Domain. 

Under /etc/bind as Root, I do NOT see a "db.example.com". I DO see 
db.root
 db.local
db.0
db.127
db.244
db.empty
named.conf
named.conf.default-zones
named.conf.local
 named.conf.options
rndc.key
zones.rfc1918

  I *think* "db.root" is my guy, however none of these files contain my MX records. I was hoping to just add my TXT record to whichever file also contained my MX records. None do. Hmmmm....

 So I think I can safely divulge that this is to add an Atlassian web service text string. Let's say they gave us this string to add: atlassian-domain-verification=12345ABCD12345EFGH 

My remaining questions are
          1) Is db.root, in fact, the file I want to add my TXT record to?

          2) Do I add the above string in this format?         IN      TXT         atlassian-domain-verification=12345ABCD12345EFGH 
                           or
                                                                                  IN      TXT         12345ABCD12345EFGH 
          Basically, do I remove everything before the "="?

          3) Can you think of a good way for me to test this externally to see if the TXT record is working/there/showing up?

Thanks!

---

### Post by SeijiSensei on 2018-07-07
In named.conf.local, or some other file there, do you have a 
```
zone "example.com" {
type master;
file "somefile";
};

```
The file "somefile" should be the zone file for example.com.

---

### Post by fatzmccracken on 2018-07-09
Good info - Ok, in my named.conf.local file, it references 3 Zones: example.com, example.net and example.org

The file I am looking for appears to be "example.com.master"

However, that file is not present. At least not in our /etc/bind folder. I ran the command "find example.com.master", with no luck.

Perhaps I need to create that file?

Thanks!

---

### Post by SeijiSensei on 2018-07-10
Try using locate.  First, update the database, then search like this:

```

sudo updatedb
locate example.com.master

```

That will search the whole filesystem.  The location of the zone files is determined by the "directory" option that should appear at the top of named.conf.local.  (Usually the "locate" database is updated daily via the script /etc/cron.daily/mlocate, but it doesn't hurt to update it manually just to make sure.)

If you don't have a zone file at all, the server wouldn't be able to resolve any names.  What happens if you run "host -t ns example.com"?  That should tell you the nameserver(s) for the domain.  If it comes up empty, then yes, you would need to build a zone file from scratch.

---

