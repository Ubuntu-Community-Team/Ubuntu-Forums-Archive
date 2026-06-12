---
title: "Auto changing user to plex"
date: 2022-05-22
forum: General Help
---

### Post by trekker182 on 2022-05-22
Hello, I am using Ubuntu 20.04 as my Plex server.  I ran into a minor problem with deleting movies via the web interface that I fixed by making the Plex user part of the admin group and making it the owner of each of my MP4s.  This fixed the issue great!  Now I'm finding that when I send over the MP4s via SFTP , the user listed is trekker182 and not plex which makes sense.  I'm trying to find a way to either auto change the user from trekker182 to the plex user upon file creation or just making a SFTP login as plex.  So far, I'm failing in both counts lol.

I tried to make a plex SFTP only login, but then I got the error user already exists.  But this is just for SFTP access?  Do users in Ubuntu all have SFTP access automatically ?  Could I just log in via Plex since there's already a user ?  If so, where would I find it's password?  For instance, my user in Ubuntu is trekker182 as well and I only see one entry in the passwd file so I'm assuming it's for both SFTP and shell?  I do see a generic SSHD user with no login, but there's no user name.
The plex user has no login and it's path is plexmediaserver which makes sense.

Second point of attack has been using incron after the fact.  I have /extmedia/Videos IN_CREATE /bin/chmod plex $# , but it's not working.  I have root listed in the allowed users file, so why isn't it working?  When I copy over an MP4 via File Zilla, the user still stays as trekker182 my SFTP user. 

Thanks for any help or suggestions.

---

### Post by TheFu on 2022-05-22
So ... ever heard of Unix groups?  The owner doesn't matter in the most simplistic solution to the problem you've described.
[Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp)
explains how to allow 2 userids to both have full access to, including delete on files.
>  Do users in Ubuntu all have SFTP access automatically
If the openssh-server is installed, then users with logins do. Users without logins, like plex, don't.  That can be further restricted to specific users in the sshd config files. How is fully documented in the manpage for sshd_config.

Never heard of incron.  I use anacron and cron.  But there is little need to deal with the userids if the users writing to the media directories are in the same group and the directories are setup as described in that link above.

Before you get too into Plex, if you care at all about privacy, switch to Jellyfin. They are similar, but different. One respects your privacy and the other does not.  Both are good at most things with each being better at some things than the other.

---

### Post by trekker182 on 2022-05-22
Thanks!  The answer was right in front of me the entire time.  Trekker182 was already added to its own group, so it still let me delete from the web interface.

This is the first time I'm hearing about Plex and privacy concerns.  I've never heard of Jellyfin, but I'll check it out for sure.

---

### Post by #&amp;thj^% on 2022-05-22
> **trekker182 said:**
>   I've never heard of Jellyfin, but I'll check it out for sure.

Good Start: [https://jellyfin.org/docs/general/administration/installing.html](https://jellyfin.org/docs/general/administration/installing.html)
And from the Core Team
[B]Posted by
u/anthonylavado
Jellyfin Core Team[/B]
There was a comment in the original Donations post, where a user asked some important questions. They wanted to know, in as much detail as possible:

    If we currently plan to implement advertising in to the platform in any way, shape or form

    If we collect user data, and if so, what do we collect and what do we do with it

Here is my response:

    No. Never.

    Not intentionally.

We do not have any third party analytics embedded in our apps at all. The closest to a central server is the repo where software and plug-ins are provided, which is hosted on DigitalOcean. We don&#8217;t get or keep any logs from there.

When you use Jellyfin/some plug-ins, you do make requests out to certain metadata providers. This varies based on your settings. This could include:
[list]
    [*]The TVDB

    [*]TheMovieDB

    [*]Open Movie Database

    [*]MusicBrainz

    [*]OpenSubtitles

    [*]TheAudioDB

    [*]FanArt

    [*]Google Books

    [*]Goodreads
[/list]
    More not listed here, depending on the plugin

We don&#8217;t include any kind of unique user code or anything in those requests, just our API key to access them. Your mileage may vary with each service, please check with them for how they handle incoming requests.

For apps on app stores, some of the platform providers send analytics based on user settings. This could be through a &#8220;Feedback&#8221; option, or when the app crashes, or when you leave a review. We cannot turn these off. You can, as a user, turn off this function on your platform.

---

