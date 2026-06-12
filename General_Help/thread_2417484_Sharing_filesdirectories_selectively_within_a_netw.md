---
title: "Sharing files/directories selectively within a network"
date: 2019-04-23
forum: General Help
---

### Post by flucoe2 on 2019-04-23
In my office, the admin people want to set up an efficient way to share files and directories selectively with the users that need access to each file/directory, and preventing other users in the same network from accessing the files they don't need. I'm not an IT person but simply an Ubuntu user, so it is very likely I don't know all the information that is necessary to define the most efficient way to do this, so I would like to ask the community's opinion on the topic. Until today, the admin people in my office have used a shared drive but the experience has been bad as they haven't been able to implement the "selective" component in an efficient way. Further, the original network had only computers that used Windows but today there are several Linux flavors, OSX, and Windows computers. In practice, people not running Windows simply don't see the shared drive in their computers, so the admin people have resorted to emailing the files to these users. In the future, the idea is to avoid having to resort to email as they want to keep the files within the office network.

What would be the best way to selectively share files/directories with specific network users, when the users may use different operative systems? In my naive view, the person that does this could use cloud-based systems and share files/directories with specific features. However, if they were to choose, for example, Google Drive, this would force Linux users to use a web browser (or at least this was the case until not so long ago). Similarly, with Dropbox, users that don't use Dropbox would need to click on an email link to access the files through a website. So, is there a better way to do this? For simplicity, we can assume that only one user (that uses Windows) will decide which files/directories will be shared with which users.

I'll be happy to figure out more details and ask questions to the people that run this, if this is needed.
Thanks.

---

### Post by TheFu on 2019-04-23
If Windows must be involved, then samba is the solution.  Setup groups of userids into specific groups, then make shares based on those groups.  This is basic IT stuff.  Samba scales to over 10K users, probably much higher than that.
Samba works best on the same LAN and shouldn't be used over the internet even with a VPN. The protocol wasn't designed for that use.

Externally hosted cloudy solutions generally shouldn't be used for corporate data, IMHO. Especially if that data is sensitive in any way. There are multiple cloudy services which can be provisioned inside a corporation. OwnCloud, NextCloud, Seafile are some examples.  I use Nextcloud here, but not for file sharing. Nextcloud has a huge ecosystem of F/LOSS addons to handle all sorts of things.  None of these care much about which OS the clients run.  Inside a company, often external _support_ contracts are needed. Nextcloud and OwnCloud have plenty of 3rd party experts very ready to help companies.

If the company needs more than just file sharing, perhaps they need document management, then there are specific tools for that like Alfresco.  Alfresco is enterprise-grade. It is a pain to deal with and not very pretty with the included webapp. Most deployments use it for a back-end only and they pay a CMS team to make a pretty front-end. Alfresco has an "open core" model where they charge for deployments that use enterprise tools, like Oracle. A few years ago, the average cost of a deployment was $250K between SW and custom development costs.  Whitehouse.gov used to be Drupal with Alfresco on the back end.

India (the country) deployed OwnCloud for govt interactions with their citizens. [https://www.itwire.com/cloud/74363-owncloud-to-help-india-build-digilocker-project.html](https://www.itwire.com/cloud/74363-owncloud-to-help-india-build-digilocker-project.html)

Regardless, the IT support guys need to handle this, unless you are planning a move to that group and want the headaches of managing these systems.  After the initial setup, it becomes a hassle, just like managing any IT server + services for end-users.

---

### Post by flucoe2 on 2019-04-23
This is great advice, thanks!

---

### Post by HermanAB on 2019-04-23
Hmm, Samba is actually very old, clunky, hard to manage and insecure.

If you want something more modern, look at Document Management Servers, such as Mayan-EDMS, OpenDocman or Alfresco.  These servers offer a web based control panel and fine grained document control.

---

### Post by TheFu on 2019-04-24
> **HermanAB said:**
> Hmm, Samba is actually very old, clunky, hard to manage and insecure.

If you want something more modern, look at Document Management Servers, such as Mayan-EDMS, OpenDocman or Alfresco.  These servers offer a web based control panel and fine grained document control.

In a business, document management can be a great tool for efficiency improvements.  I spent about 10 yrs on an enterprise architecture team setting standards for document management.  We looked at everything - free, cheap, expensive, custom built.  We got sucked into multiple deployments, some of those costing $millions.  I've administrated Alfresco, just looked at both OpenDocman and Mayan-EDMS, used Documentum, FileNet, DocuShare, Sharepoint and about 10 others.  

All document management systems need a librarian to ensure the library organization is correct and that metadata for each document is correct.  I learned long ago to never trust user-created document metadata. They can't be bothered to change any of that data, so whoever creates the first document will appear to have created all the documents going forward. Of course, if systems are creating the document, then your team will ensure the metadata is correct.  

The librarian is needed to ensure every team inside the organization understand how their documents should be stored, mainly from an access control perspective, but also for processes, standards, and personal file areas.  The goal is to only have enough documents to do the job and to make annual document cleanup as easy as possible, following the company and department data retention standards.  Usually, companies only want to keep documents for 7 yrs or less, though a few have to be kept forever due to govt regulation.  Keeping documents too long is a legal liability for every organization. Best to avoid that.  It is better to be able to point to a data retention policy when the lawyers come knocking that says we retain that type of document for 1 year before deletion, but the teams each have to actually delete the files when the retention period expires.

If you need fully enterprise-class DMS, expect to pay, and Alfresco with customizations is probably the most effective.  

If you need lighter, more flexible DMS, Xerox DocuShare is freakin' amazing for the price (when compared to other ECM solutions). From purchase to starting full use was just hours. It isn't about the GUI, it is about storing and finding documents in an enterprise.

Sharepoint's only good point is that MSFT will give it to you.  We found that at least 1 person per team would go crazy trying to make pretty pages. The search facility sucked.

OwnCloud and Nextcloud don't do DMS.  Their search facilities suck. Search addons don't make it better, unfortunately.  These are best for personal storage and for tiny teams that don't need to share outside their teams.  Basically, they are samba shares with better client support and can be used over the internet with a real VPN.  

The real power in Nextcloud is their addon applications. I barely use the file storage stuff, since I have other solutions for that and when I'm travelling, I'm usually offline unless wifi connected with a full VPN into the LAN back at the office.  OTOH, about 6 weeks ago, a nextcloud 1-click update broke a few of the addons making access to some data impossible. It is still broke.  We had been moving the addressbooks and calendaring and tasks into Nextcloud.  None of them worked as well as our prior solution, Zimbra.  All the tasks people entered are gone. No idea what happened.  Initially, we restored everything to the day prior to the upgrade and had people grab what they needed.  Then we did it again and it broke in the same way.

There are lots of options today.

---

### Post by flucoe2 on 2019-04-24
Wow, this is tons of information. Thanks for all the details.

---

### Post by SeijiSensei on 2019-04-24
If you want to share files with both Windows and Linux users, you can run an [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") server alongside Samba.  My home office server runs both so I can see the same shared directories from both OS's.  Authentication becomes a bit more tricky though especially if the number of users grows.  You might want to consider a centralized authentication server using [LDAP]("https://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol") which both [Samba]("https://help.ubuntu.com/lts/serverguide/samba-ldap.html.en") and [NFS]("http://support.huawei.com/enterprise/docinforeader!loadDocument1.action?contentId=DOC1000042685&partNo=100122") support. You could run this software on the same machine running NFS and Samba.

---

### Post by HermanAB on 2019-04-24
Wow, running NFS and Samba at the same time, sounds like a Rube Goldberg Machine, that will give you all the problems of both systems.

---

### Post by SeijiSensei on 2019-04-25
Not at all, at least in my little implementation.  I rarely use Windows but have one in a VirtualBox VM that mounts my home directory with Samba.  I store anything that matters on the server and can see the files from both operating systems.  I have just a couple of users so I use simple authentication on Samba with smbpasswd and, of course, normal authentication via /etc/shadow on NFS.

---

### Post by HermanAB on 2019-04-25
BTW, I would not use two network file systems (Samba and NFS) at the same time, since I am not sure what would happen if two users would access the same file at the same time.  Also, Windows does have a free NFS client.  You can download it from the Microsoft Technet web site.

Since NFS is much easier to set up and manage than Samba, that would  be my preference.  However, Windows has native support for Anonymous FTP, which is even simpler than NFS.  So if you want a super easy file server, then nothing beats anonymous FTP.

---

### Post by TheFu on 2019-04-25
I've never had any issues with both NFS and samba in a business with 30 people accessing the same files. If there is a file lock from a client, then that works as expected, provided the clients support it.  If there isn't, the last "write" wins.  This is normal Unix behavior.  

We used NIS at the time to manage Unix users (mid-1990s). I wouldn't do that today. Last time I needed centralized user management, I used LDAP with POSIX extensions in an existing LDAP implementation running inside a Zimbra server.  I would implement LDAP completely separate using FreeIPA if I had to do it all over again.  Every Zimbra upgrade requires removal of the POSIX extensions from the LDAP schema, then putting those back after. It is a pain.

From Windows, I use **WinSCP** as an sftp/scp client, unless I'm on the LAN and have samba setup already.  All Unix/Linux systems use either NFS or some other protocol like rsync/scp/sftp.  Plain FTP isn't something I've allowed for about 20 yrs.  For me, the only valid reason for plan FTP would be for seeding new servers, but HTTP or tftp can be used for that easier, without confusing people by having any plain FTP running.  It is much easier to have IT understand that plain FTP isn't allowed, period, than it is to have 5 exceptions where the risks are minimal. It also makes life much easier to explain to non-technical employees that plain FTP won't ever be used in our company.  Simple explanations often trump things.

---

