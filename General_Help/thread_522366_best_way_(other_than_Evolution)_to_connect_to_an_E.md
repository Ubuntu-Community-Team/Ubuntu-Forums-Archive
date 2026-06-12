---
title: "best way (other than Evolution) to connect to an Exchange server?"
date: 2007-08-10
forum: General Help
---

### Post by hotani on 2007-08-10
Here's the problem: the Evolution-Exchange plugin is a steaming pile of crap. If you are a developer of said plugin and reading this, I make no apologies. It is broken, it crashes, it brings down Evolution on my system every day at least once. Usually this happens when I'm typing a name in the "To:" field and it attempts to auto-fill the name. Sometimes this seems to work, then the e-mail won't send. It goes away like it sent, but then an error appears and there is no way to get it back. 

Before you post, please note:
1- Don't give me that "file a bug..." crap either. The bugs are filed. I'm looking for input here.
2- If you are going to post shifting blame to Microsoft, save your time. We all know MS sucks, and they pride themselves in **in**operability between systems. They suck, yes. However, with the amount of development firepower in the open source community, why is the only available option this broken plugin for Evolution? Why is this not a top priority? Look how many media players there are!!! When a business user wants to use linux on the desktop, what tools do they need? Office and e-mail. What is the most common e-mail server? Priorities, people.

What are the alternatives? Is there another mail client that will connect to an Exchange server? Should I just give up on using Exchange through a mail client and use the web access? The web access that is built from the ground up to work ONLY in IE? Fortunately it (barely) functions in Firefox. Or I can use vmware *shudder*. 

Please tell me there is an alternative. A magical e-mail client for linux that can connect to Exchange without making me want to stab myself in the eye with a rusty fork. Anyone?

---

### Post by aysiu on 2007-08-10
I know this doesn't help you, but I've had better luck connecting to my workplace's Exchange server using Evolution in Ubuntu than using Outlook in Windows.

---

### Post by hotani on 2007-08-10
Outlook not only connects for me, but allows access to all the shared services such as calendars and tasks. I do think it is great that we are able to connect at all to Exchange from Linux, I just wish that connection was more stable.

On some systems it does not cause problems. Unfortunately the one that has the most issues is my primary work system.

---

### Post by Majorix on 2007-08-10
Have you tried Thunderbird? It is a part of the mozilla suite.

---

### Post by aysiu on 2007-08-10
I've tried Thunderbird, and I haven't seen its ability to connect to an Exchange server, even through an extension.

---

### Post by Lorenzo1449 on 2007-08-16
I'm curious to know if anyone has tried Novell Evolution 2 with Ubuntu. I know it's not free but I would be willing to pay just to get a decent exchange compatible mail client.
[http://www.novell.com/products/desktop/features/evolution.html](http://www.novell.com/products/desktop/features/evolution.html)

Nigel Regan

---

### Post by vinodis on 2007-08-16
Sorry to say this:-
There is no decent Exchange Server Clients for Linux yet. Evolution is way behind. It does not even have an import function for .pst files. Other PST import options through Thunderbird just breaks when the mails are in Outlook specific format. Evolution does not handle the calendar and Tasks well. Alltogether there is nothing out there to help replace Outlook for you.
I have tried running Outlook 2003 using CrossOver Office. It runs. But does not do a decent copy&paste between other applications. It crashes often too. 
Finally I am into seamlessly virtualizing WindowsXP using a headless VirtualBox VRDP instance. It works for me.

---

### Post by igknighted on 2007-08-16
Kontact can connect to exchange, can't it?

---

### Post by vinodis on 2007-08-16
'Connecting' is one thing.. But seamless Exchange server integration is something else..
Most of the Linux Clients for Exchange Server uses the OWA ( Outlook Web Access) as the base method to connect. That has limitations. Most of the Organizations does not support IMAP either.

---

### Post by bogolisk on 2007-08-16
> **vinodis said:**
> Sorry to say this:-
There is no decent Exchange Server Clients for Linux yet. Evolution is way behind.

True

>  It does not even have an import function for .pst files. Other PST import options through Thunderbird just breaks when the mails are in Outlook specific format.

Hmm, PST is the outlook's local file format isn't it? It has nothing to do with Exchange Server.

At my work, Evolution (on RHEL) and Exchange seems to work out ok. But the admins are experienced ex-Unix admins and they went out of the way to make it work with Evolution (even demanding patch from Microsoft.)

---

### Post by vinodis on 2007-08-16
Interesting to note..
Do you have more details of those patches and workarounds? If so please consider sharing. 

Yeah.. PST is an Outlook specific client storage format. But that's how your exchange data is captured for posterity. If Evolution wants to be a TRUE Outlook replacement, it should sport a good .PST importer. The route through importing to Thunderbird and then to Evolution do not work if the mails are in MS specific richtext format. Outport is also dated.

---

### Post by bogolisk on 2007-08-16
> **vinodis said:**
> Interesting to note..
Do you have more details of those patches and workarounds? If so please consider sharing. 

I don't think it would be possible, those are patches for the Exchange Server 2003 software. They are part of an expensive support contract with MS.

> 
Yeah.. PST is an Outlook specific client storage format. But that's how your exchange data is captured for posterity. If Evolution wants to be a TRUE Outlook replacement, it should sport a good .PST importer.

I don't think evolution/connector ever claimed to be an *Outlook replacement*. It claimed that: with it, you can connect to an Exchange server for Mail and Calendar.

---

### Post by Samuelh3 on 2007-09-04
I have to agree. Evolution to date has been less then perfect. Considering how important it is for business users to be able to collaborate with other users using Exchange one would think a good client would be available. The main reason I still keep my Vista machine around is the Outlook client is by far easier to work with, faster as well. I just switched over to Linux and as much as I use email, its almost a show-stopper. As a newcomer to Linux finding one would be very beneficial.

---

### Post by perfecttao on 2007-10-12
Ok....so MS won't allow third parties to connect to their mail server using native modes....so turning this problem on it's head.....can anyone out there recommend a good, open source mail server that supports all the calendaring functionality available in Exchange?

I'm looking for SSL webmail, Shared Diaries, tasks, appointments, collaboration and push email to Mobile devices....

So annoyed with the whole integration issue, plus an increased headcount at our offices now means increase in licencing costs that i'm seriously considering a major overhaul (currently with 3 x Windows server 2003, Exchange 2003 and 40 CALS for windows and Windows Licences!!) :(

P

---

### Post by reza81 on 2007-10-12
> **bogolisk said:**
> True



Hmm, PST is the outlook's local file format isn't it? It has nothing to do with Exchange Server.

At my work, Evolution (on RHEL) and Exchange seems to work out ok. But the admins are experienced ex-Unix admins and they went out of the way to make it work with Evolution (even demanding patch from Microsoft.)

tweak the patch & post :lolflag:

---

### Post by Palmyra on 2007-10-14
So....does Exchange work with Thunderbird at all?  I'd prefer using open source applications, and so far, Thunderbird hasn't been all that help, but it could be that I am doing something wrong.  We don't really have an IT team at work, and I don't want to bother anyone to get this to work.

---

### Post by euler_fan on 2007-10-14
> **Palmyra said:**
> So....does Exchange work with Thunderbird at all?  I'd prefer using open source applications, and so far, Thunderbird hasn't been all that help, but it could be that I am doing something wrong.  We don't really have an IT team at work, and I don't want to bother anyone to get this to work.

It's possible to use Thunderbird for email access if IMAP/SMTP access is available. At my uni they use MS Exchange and offer Outlook Web Access as the primary means of accessing it, but also have imap/smtp servers accessible for people (mostly faculty/staff who use Macs I suspect) and used to publish explicit instructions on how to connect to them. This works for email at least. I connect to the IMAP server through Thunderbird. Sorry if that's not more help.

Please forgive if this is an amateurish sort of suggestion for a piecemeal solution for the person asking about an overhaul from Windows to OSS: Would using an IMAP/SMTP server for email, an LDAP server for directory and an iCalendar server for calendaring, etc. work? In Sunbird/Lightening for you can sync/publish you calendar with in iCal format to a server and with Lightening there is even the ability to offer Outlook style meeting requests. IMAP/SMTP and LDAP are already completely compatible.

---

### Post by perfecttao on 2007-10-15
> **euler_fan said:**
> 
Please forgive if this is an amateurish sort of suggestion for a piecemeal solution for the person asking about an overhaul from Windows to OSS.

Not a problem - all suggestions gratefully received :)

---

### Post by freelsjd on 2007-10-16
Using Evolution up to and including 2.18, worked flawlessly for me at work with the Microsoft Exchange 2003 server.  then they upgraded to the Exchange 2007 server and it broke all this so bad that it would not even login.  I think that the OWA web access went away with Exchange 2007 ?  Anyway, the work around is actually better for me:  I converted over th IMAP connection to the Exchange 2007 server.  This takes care of the e-mail.   then for the Global Directory (or what ever they call it), I set up ldap and that fixed that.  The only thing I do not have is the calendar input.  I can get calendar output pop ups, just can't set anything in the calendar myself.  If I want to input to the calendar or view the calendar, I have to access via the web.

I agree that the Linux community needs to conquer this problem.  I just do not understand why "they" think that Microsoft exchange server is the best alternative for e-mail, calendar, directory,  etc.  Just crazy.

---

