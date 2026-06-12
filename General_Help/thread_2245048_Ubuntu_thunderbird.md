---
title: "Ubuntu thunderbird"
date: 2014-09-20
forum: General Help
---

### Post by rbmoler on 2014-09-20
I have a strange problem with Thunderbird on Ubuntu 14.04LTS.  The machine is dual booted with Win7 & Ubuntu 14.04 LTS.  The profiles for both Thunderbird and Firefox are on a media/data HD so the Thunderbird in the two OPSs uses the exact same profile.

In Ubuntu and Win7 Thunderbird receives E-Mail fine

Not so when sending mail.  Everything works normally in Win7, but in Ubuntu Thunderbird has developed a serious hickup.  When I insert an email address in the **To:** box, most of the time it shows up in _red_ as though it is not a valid email address.

Even when I do get a normal black address I cannot get the message to send unless it is less than about 5 lines long. Such short messages are sent successfully regardless of the indication that the E-Mail address is invalid.  (Red).  Attachments also halt the sending of the message.

The sending box opens, it may show some % of the message has been sent, but it just sits with the sending icon running until I finally get the "Sending of message failed.  SMPT timed out," followed by the usual message to check various things about how I'm connected to Verizon's DSL line. 

There are now 2 Ubuntu computers in my household that have the same issue.  It started about 4 days ago and I've spent the time trying to isolate it which seems to be a Thunderbird/Ubuntu thing.

If this is a problem specific to Thunderbird I assume I could remove thunderbird and reload it.  Retrieving the profile is not much of a problem.  Still I'd like a little advice before I do that.

---

### Post by TheFu on 2014-09-21
Without carefully reading the thunderbird source code, I don't think anyone can help ... 
but Linux systems expect linux storage with UNIX-style permissions.  I strongly suspect THAT is the real issue here. Put the .thunderbird directory under your HOME on a linux file system, NOT NTFS/vfat/fat-whatever, see if that fixes it.

---

### Post by oldfred on 2014-09-21
I stopped using XP about 2 years ago. But I had a shared NTFS data partition with both Firefox & Thunderbird profiles in that shared data partition since 2006. It still is in the NTFS partition as I have not reorganized yet to eliminate my NTFS partition.  I have not had any issues in Ubuntu with Thunderbird in a NTFS partition, but have not opened with XP for a long time. But it does get opened with different installs of Ubuntu that may have slightly  different versions of Thunderbird.

---

### Post by amanchesterman on 2014-09-21
rbmoler: I think you are mistaken in believing that an address in red in the 'To:' box is a warning that 'it is not a valid email address'. It is standard Thunderbird behaviour and does it on my machine also, which only has a single partition (not shared with Windows). According to the Thunderbird help pages, the red font simply indicates that the email address has not been stored in the address book. I haven't checked that systematically because the red font doesn't bother me much, but certainly some of the addresses I use often (which are in my address book) appear in black type whereas others appear in red, even though they are just as 'valid'.

Why you are getting this indication in your Ubuntu version of Thunderbird and not in the Windows one, I don't know, but I suspect it has to do with oldfred's point that the versions are probably subtly different.

---

### Post by TheFu on 2014-09-21
> **oldfred said:**
> I stopped using XP about 2 years ago. But I had a shared NTFS data partition with both Firefox & Thunderbird profiles in that shared data partition since 2006. It still is in the NTFS partition as I have not reorganized yet to eliminate my NTFS partition.  I have not had any issues in Ubuntu with Thunderbird in a NTFS partition, but have not opened with XP for a long time. But it does get opened with different installs of Ubuntu that may have slightly  different versions of Thunderbird.

Oldfred - do you really mount it or use gvfs?  I've been burned with gvfs and a few different programs.

Moved .thunderbird profiles around between Win, Linux and OSX without issues (provided no binary addons are there). Worked an issue with someone last year trying to share the same profile concurrently via NFS too. It surprised me that didn't work well.

---

### Post by rbmoler on 2014-09-21
OK.  I appreciate the input.  But to keep things as simple as possible it is important to note that the main issue is the refusal of thunderbird to send any email that is larger than a few lines - period!  That means that I cannot reply to _any_ email that I receive because the size of the received email with it headers etc. already exceeds the size that *my* thunderbird in Ubuntu will allow to be sent.

Secondly.  The behavior began to occur _only_ less than a week ago (Thursday or maybe Wednesday Sep 17).  Nothing like this occurred from the time Ubuntu 14.04 LTS became available (I downloaded it to this machine within days of its availability and as the upgrade to another machine then running 13.04 LTS when that upgrade became available.)  It *may* have been after I installed an update to both machines that included some Thunderbird updates.  If it had happened in a windows environment I would have suspected a virus or some kind of malware, but not in both machines, one of which is rarely used for anything except emails to family and for writing using LibreOffice.

I could certainly let Thunderbird start over and create a new profile located in the default Ubunta location and see if that works correctly.  I think it's possible to migrate address books, emails, and sent messages to the newly created profile.  It's possible in windows.  Still it seems unlikely that something in the profiles folder has anything to do with this behavior.  The fact that it occurred almost simultaneously in two different machines is very suspicious to me.

---

### Post by dragonfly41 on 2014-09-21
In Thunderbird look at "Outgoing Server (SMTP)" .. at the bottom of menu of Account Settings.

Check the smtp settings.

Can you try an alternative smtp server?

Can you ping your (default) smtp server?

Any status reports from your mail service provider (look at their web site for status)?

---

### Post by TheFu on 2014-09-21
Is the storage for draft email almost full?   probably not, but I have to ask. Perhaps out/low of inodes?

You can simply copy the ntfs .thunderbird/ directory to your Linux machine. 

Could the mail server storage be full to your quota level? I only use IMAP, so all email is on the server, but I've never let it get near full.

Doubtful any of these things are your issue, but ... maybe?

---

### Post by dragonfly41 on 2014-09-21
Just an added note to my earlier post.  
Since you are reporting problems in sending .. not receiving .. I'm concentrating on smtp.

Here is a useful tool to test your smtp server.

[http://mxtoolbox.com/diagnostic.aspx](http://mxtoolbox.com/diagnostic.aspx)

---

### Post by oldfred on 2014-09-21
I actually mount my data partitions via fstab. 
And then I edit profile.ini to find the profiles.

I have not tried connecting from more than one computer, just different installs in the same computer.
I do use NFS only to copy my profile to my laptop when I travel & then when I return.

---

### Post by s9032g@comcast.net on 2014-09-21
You might take a look at this:

[http://kb.mozillazine.org/Cannot_send_mail](http://kb.mozillazine.org/Cannot_send_mail)

---

### Post by rbmoler on 2014-09-21
OK, I have done some things and will do some more with a little advice.

First the two computers are entirely separate.  One (the older 0ne) is dual booted with XP.  The other, this one, is dual booted with W7.  On the older one with XP, Ubuntu 13.04 LTS was installed in Jan of 2014.  It has worked perfectly, including after the upgrade to 14.04 LTS, with the profile for Thunderbird on a separate HD with ntfs format.  This box had Ubuntu 14.04 LTS installed as soon as it was available.  It too has thunderbird installed on a separate common ntfs hd named /media/robert/data  and had worked perfectly until last Wednesday.

I tried the diagnostics suggested by dragonfly21.  There was nothing amiss except that verizon doesn't support encryption.

My next step is going to be to copy the profiles folder to Ubuntu then edit the profile manager to create two profiles so that I can determine if the location of the profile folder is really at fault.  It's hard to believe it is, since having it located on an ntfs formated separate drive worked perfectly for the past 7+ months.  Nothing else on that drive acts funny.  I can access all of my text files, pictures, videos, lots of documents from the internet, and all of my financial information.  Firefox doesn't have a problem with my bookmarks which are on than drive.

The advice I need is where I should put a copy of the profile directory.  My facility with the file system in Ubuntu is very limited.  I'm very much a novice for that and at 81 my learning curve is a bit steep.  A step by step would lessen my stress.  On the ntfs disk the folder is** /media/robert/data/Mozilla/Thunderbird Profiles/Profiles**. I presume it would be adequate to simply copy the **/Thunderbird Profiles**/**Profiles** sub-folder and put it in the appropriate location in Ubuntu.  Then open thunderbird -P and create a new profile that points to that location.  That way I haven't done anything irrevocable.

I'll be back.  Thanks for your help and for giving it a try.

---

### Post by oldfred on 2014-09-21
More info on profiles.

I start Thunderbird once just to create a default profile. Then I copy in a new profile.ini that refers to my actual profile in my NTFS partition. Default location in Ubuntu is .thunderbird in your /home. You have to turn on show hidden files to see it. In .thunderbird is profile.ini and the profile that it creates (or your copy or both). Profile will be a "bunch of letters".default like abcdefg.default.

More info on profiles.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by rbmoler on 2014-09-21
Moving profiles and creating new profiles in thunderbird is relatively easy.  I'll copy the existing profile to /home.thunderbird. then open a terminal. and run thunderbird -P, give a name to the new profile and brouse to the folder in ubuntu  that contains the profile.xxxxxxx file and activate it. It will have the same 8 characters extension.  The profile folder in my ntfs HD is not hidden.

After that Thunderbird asks which profile I want to use when I open thunderbird.  No problem.  It really doesn't matter where the profile is located if thunderbird can find it.  I know that from experience when I created two profiles located on two separate discs (the hidden default profile and a new unhidden profile that I created on my media/robert/data HD.  I have little hope that this will work, but I'll try it.  No stone left untuned.

---

### Post by dragonfly41 on 2014-09-22
Reading a bit more on Verizon ...

[http://forums.verizon.com/t5/Verizon-net-Email/VERIZON-Mail-Server-Settings/td-p/568055](http://forums.verizon.com/t5/Verizon-net-Email/VERIZON-Mail-Server-Settings/td-p/568055)

What are your Thunderbird smtp server settings?

smtp.verizon.net port 465
or
outgoing.verizon.net port 465    (outdated)

read here for latest ...

[http://www.verizon.com/Support/Residential/Internet/fiosinternet/Email/Setup+And+Use/QuestionsOne/124289.htm?CMP=DMC-CVZ_ZZ_ZZ_Z_ZZ_N_X322](http://www.verizon.com/Support/Residential/Internet/fiosinternet/Email/Setup+And+Use/QuestionsOne/124289.htm?CMP=DMC-CVZ_ZZ_ZZ_Z_ZZ_N_X322)

> 
Please Note: Verizon has recently updated our email client settings to improve security. Please review the settings below to verify that your email software client (e.g. Outlook, Outlook Express, etc.) has the most recent configuration.


...

Incidentally, if you are using POP3 instead of IMAP for incoming mail, then as a precaution I would regularly  backup your Thunderbird profile to avoid losing your archived POP3 email.

pop3

[http://www.verizon.com/support/residential/internet/fiosinternet/email/setup+and+use/questionsone/85540.htm](http://www.verizon.com/support/residential/internet/fiosinternet/email/setup+and+use/questionsone/85540.htm)

Personally I use IMAP setting for incoming mail so that I can reload archives from my ISP provider if ever I lose a Thunderbird profile in a crash.

---

### Post by rbmoler on 2014-09-22
Glory be, Dragonfly41!  I think you've solved it.  My Settings are outgoing.verizon.net port 0. (default)  I assume that I simply enter the port number in the space which now has zero.  Is it appropriate to simple edit the smtp setting so that I don't have to go through the hassle of making sure I'm entering the correct password?

---

### Post by TheFu on 2014-09-22
> **rbmoler said:**
> Glory be, Dragonfly41!  I think you've solved it.  My Settings are outgoing.verizon.net port 0. (default)  I assume that I simply enter the port number in the space which now has zero.  Is it appropriate to simple edit the smtp setting so that I don't have to go through the hassle of making sure I'm entering the correct password?

yes. that should work.

---

### Post by rbmoler on 2014-09-23
Ugh!  Didn't work.  I changed the default outgoing server to smtp,verizon.net with port 465.  Couldn't send a one word message to myself.  Same old symptom.  Server timed out.  Changed it back to outgoing,verizon.net and port 465 the Ubuntu default.  Still no luck.  Finally back to what I think was the original- outgoing.verizon.net, port 587.  That worked the same as before - short messages were sent, Five lines timed out withoout sending.

Back to start without passing go.  I guess I'm left with re-installing Thunderbird from scratch.

---

### Post by dragonfly41 on 2014-09-23
> I changed the default outgoing server to smtp[COLOR=#ff0000]**,**[/COLOR]verizon.net with port 465

Is that a typo error .. should be dots throughout .. no comma.

Try going to command terminal and typing command ... **ping smtp.verizon.net**

what do you see in terminal?

[later edit]

In Outgoing Server (SMTP)
edit default smtp server

have you set 

Server Name: smtp.verizon.net

Port: 465

Connection security: SSL/TLS
Authentication method: Normal password

==============================================

[yet further edit]

Please read this again ...

[http://www.verizon.com/Support/Residential/Internet/fiosinternet/Email/Setup+And+Use/QuestionsOne/124289.htm?CMP=DMC-CVZ_ZZ_ZZ_Z_ZZ_N_X322](http://www.verizon.com/Support/Residential/Internet/fiosinternet/Email/Setup+And+Use/QuestionsOne/124289.htm?CMP=DMC-CVZ_ZZ_ZZ_Z_ZZ_N_X322)

> 
Note: If you are an HSI (DSL) customer with a Westell or Actiontec modem (except Actiontec GT784WG) and using its firewall, you may need to turn your firewall settings to &#8216;Low&#8217; for new email settings to work.

...

Try an Automatic Solution

Use Verizon Troubleshooter(for consumer email accounts only)

[http://www.verizon.com/support/residential/internet/fiosinternet/email/setup+and+use/126652.htm](http://www.verizon.com/support/residential/internet/fiosinternet/email/setup+and+use/126652.htm)




Can you send email using WebMail (via browser) instead of Thunderbird?

[http://www.verizon.com/support/residential/internet/fiosinternet/email/troubleshooting/questionsone/85631.htm](http://www.verizon.com/support/residential/internet/fiosinternet/email/troubleshooting/questionsone/85631.htm)


Here is the Verizon forum where you might get support.

[http://forums.verizon.com/t5/Verizon-net-Email/pop-verizon-net-and-smtp-verizon-net-not-working/td-p/632311](http://forums.verizon.com/t5/Verizon-net-Email/pop-verizon-net-and-smtp-verizon-net-not-working/td-p/632311)



**One possible solution .. use alternative SMTP (relay) server.**

On occasions I have hit problems in using SMTP server settings connected via other than my home account.  My SMTP outgoing has been blocked.

To get round this obstacle I had to use Dyn.com mailhop relay service.

Dyn.com mailhop service is not free but where needed provides a different route for sending email e.g. behind a blocking filter or firewall.

There is a 14 days free trial period.

---

### Post by rbmoler on 2014-09-23
Thank you!  I'm getting a little senile I guess.  It was the need to change the connection security from none to SSL/TLS that was the problem.  I simply hadn't paid enough attention to Verizon's original message regarding the change in security.

The ping of smtp.verizon.net resulted in "(206.46.232.100) 56(84) bytes of data"  I guess it doesn't matter.  The comma[COLOR=#ff0000][/COLOR] rather than a dot in my message was just a typo.

Problem solved. Sorry I wasted a lot of your valuable time on something I should have figured out myself.  I'll so indicate.

---

