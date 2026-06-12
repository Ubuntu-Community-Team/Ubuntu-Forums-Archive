---
title: "Thunderbird and Gmail - your advice please"
date: 2013-11-27
forum: General Help
---

### Post by ELMIT on 2013-11-27
I used to have Thunderbird with Google connected via POP3 with left messages on the server. 
All messages are on my hard disk and I could easy separate them into different folders for years and months.

I have many email accounts, but my two email accounts with Gmail have emails since 2003 and they are really big.


Unfortunately I lost a hard disk, so all my POP3 emails (25GB !!!) are gone. To get quickly running again, I use now IMAP. However, as soon I search anything (receiver, subject) then I can go for lunch. I will not get back Thunderbird for a long time.

What is your advice to solve that problem. Use POP3 again or is there a setting in Gmail that would help? Since I use Enigmail, another client would not be an option.

bye

Ronald

---

### Post by DuckHook on 2013-11-27
No setting I know of would help. Perhaps a more knowledgeable user can give you another alternative, but what follows is what I know:

I'm sure you probably realize this, but the problem is not finding the right setting, but rather, your positively obese e-mail account. When you were using POP3, you were basically counting on luck that you would never actually have to synchronize the account. When luck ran out and you had to sync using IMAP, 25Gigs is like asking your e-mail client to swallow a whale. I didn't even know that Gmail allowed that much bloat!

The best practice is to remain synced at all times by using IMAP from the start. In my opinion, POP3 is an obsolete protocol that no one should use anymore. It is further worsened by the fact that it has absolutely no security and your e-mail is transferred in the clear. Depending on the version and settings, IMAP encrypts e-mail during transfer and g-mail certainly does so by default. Glad to know you are using Enigmail. All the stranger that you kept with POP3 for so long.

For your particular circumstances, I would consider setting up TBird on a separate computer, leaving it on and using IMAP to sync over days if necessary. Hopefully, neither Gmail nor TBird will time out. If either does, it isn't that hard to reset the connection and start the process again. If it's a one-time thing and you don't have a problem with everything coming over in clear text, then I suppose that you can also POP3 it, but this time take it off the server (frankly, this procedure is fragile, danger-fraught and gives me the willies). Then archive your e-mail account in manageable pieces over time and reduce your Gmail dependency/exposure. You will need to set up a good backup strategy so that another HDD crash doesn't kill you (you won't have everything left with Gmail anymore--but you are discovering that leaving everything on some distant server doesn't mean that it's really accessible anyway). Crazy coincidence, but I just posted [this]("http://ubuntuforums.org/showthread.php?t=2190532&p=12859753#post12859753") on backups just a moment ago on a separate thread. If you set up your archive on the NAS it will always be just as accessible to you as now, but under your local control (and backed up!)

---

### Post by ELMIT on 2013-11-27
Thanks for your hints.

I use a paid account and some free accounts, so I can come at that large size.

I like the idea to archive PARTIAL, but if I go to Google web interface and archive it puts all into ONE folder. I guess it would be possible to rename then the Archive folder, which would be not synced and do that for each year to get a yearly archive.
Further I would like to backup these Archived years onto a DVD. 

Any hints on that?

---

### Post by DeMus on 2013-11-28
I also still use POP3 and love it more than IMAP. I have mails going back to 2008 which I don't want to lose.
In Thunderbird I have an archive folder with subfolders per year, each having an inbox and a sent items box. It is pretty easy to look for something, folders are not that big this way.
On Gmail I delete my mails after retrieving them, so I keep my free account far below the limit.
Every Sunday I make back-ups on an external hard disk so nothing gets wasted. Plus I have my mails at home instead of on a server somewhere.

No idea why POP3 should be obsolete? Because of the cloud? Ridiculous.Who wants his private stuff in the cloud anyway where anyone can have a look? Certainly not me.

---

### Post by DuckHook on 2013-11-28
Do not archive using Google Web Interface! Archive using T-Bird functionality!

Actually, you can create an archive directory tree as complex as you like. I've got my archives sorted similar to your stated preferences--sorted by year and month. You also have the option of keeping your exact current folder structure. Instructions [here]("https://support.mozillamessaging.com/en-US/kb/archived-messages"). And if you later reattach these archives back to your "Local Folders" account, you can access it and search through the archive tree just like you search through your standard e-mail tree.

The key concept here is that what T-Bird calls "archives" are not really archives (at least, as geeks technically use the term). Instead, it is just standard T-Bird e-mail files stored in a directory of your choosing *that T-Bird does not sync with the remote server*. In all other respects, they are mail files. [Here]("http://email.about.com/od/mozillathunderbirdtips/qt/et_archive_mail.htm") is a how-to showing you how to set up a set of archive folders under the "Local Folders" mail account. The trick that Linux users can use and that is not explained in the how-to is: don't *move* the archive directory from your desired location back into the T-Bird directory; *symlink* to it instead. This keeps your archives in a separate directory that is easy to identify, isolate and back up. For example, you may wish to create a *~/mail_archive* directory to keep all your archived stuff. If you want to spin any of these off to a DVD, then use deja dup and, bingo... done. But with HDD space so cheap these days, why bother deleting? In my case my archives are stored on a NAS, but I keep my archives on there forever and backup just for data safety, not to regain space.

Provided you are fully IMAPed, it is easy to sort by date, select by month, then drag and drop from Gmail to "Local Folder" archive. And because you are IMAPed, each mail that comes off the mapped folder is actually deleted on the server (you must do this with each _mapped_ folder or it's left on the server!). It really is just that simple. Maintaining this habit keeps my Gmail account down to around a hundred MBs. I find that I want at least a few months of mail on the server that I can access with my mobile devices, but anything more than four months old isn't something that I can deal with while on the run anyways.

---

### Post by DuckHook on 2013-11-28
> **DeMus said:**
> No idea why POP3 should be obsolete? Because of the cloud?Because:

1. It has no encryption. All transmissions are clear text,
2. Has really primitive error checking,
3. Is incapable of synchronization,

I consider any one of those drawbacks to be severe. Taken together, I consider them deadly. But I don't insist. Different strokes for different folks.

> Who wants his private stuff in the cloud anyway where anyone can have a look? Certainly not me.Most emphatically agreed.

---

### Post by ELMIT on 2013-12-02
I installed Thunderbird on my desktop with POP3 and try to download all messages.

I cannot find the limitations settings, but it does only retrieve all messages since May 4, 2013. 

How can I get all the old emails, to be able to move it to a DVD?

---

### Post by DuckHook on 2013-12-02
I have no idea. Didn't even know there was such a limitation. I don't use POP3 so hopefully someone who does can step in here. You might also have some luck posting on the Mozilla forums dealing with T-Bird. I *think* I know how to do this using IMAP, but frankly have never tested it because I don't leave e-mails on my servers for more than 6 months. And in any case, I have no idea if other limitations would come into play on a 35 GB e-mail account.

Whatever you do, make sure that you haven't inadvertently set your POP3 settings to delete anything on the server older than 6 months.

---

