---
title: "How to download Wordpress websites from Godaddy server to local desktop PC"
date: 2018-03-06
forum: General Help
---

### Post by satimis on 2018-03-06
Hi all,

Please advise how to download Wordpress websites from Godaddy server to Oracle VMs on my desktop PC.

Websites hosted on Godaddy - Linux, domains and sub-domains
Desktop PC 
- Host Ubuntu 16.04 desktop
- VMs, Ubuntu 16.04 desktop
- Virtualizer - Oracle Virtualbox

I did that before via FileZilla, about 10 years ago and the download websites are still running on VMs of my desktop PC.  Unfortunately I couldn't find the relevant documents on my database.  I have about 40 websites, all hosted on Godaddy server, but not all download to one VM, about 3~4 websites on one VM.

On local browser the websites can be browsed running "localhost/domain" (or sub-domain).  On remote browser (in my case, on Host browser) they can be browsed running "internal-ip/domain (or sub-domain).  They are still working but I haven't updated them for long time.

I don't know whether there are new methods for downloading them to VMs on my desktop PC?  Kindly advise.  Pointers would be appreciated.  Thanks in advance.

Regards
satimis

---

### Post by #&amp;thj^% on 2018-03-06
I've never used them but this looks promising: [https://www.youtube.com/embed/AF121v_zhug](https://www.youtube.com/embed/AF121v_zhug)
i was also just reading up on this just before you posted....what are the chances? :D : [https://ca.godaddy.com/help/install-wordpress-on-your-linux-hosted-domain-using-cpanel-16038](https://ca.godaddy.com/help/install-wordpress-on-your-linux-hosted-domain-using-cpanel-16038)

---

### Post by satimis on 2018-03-06
> **1fallen said:**
> I've never used them but this looks promising: [https://www.youtube.com/embed/AF121v_zhug](https://www.youtube.com/embed/AF121v_zhug)
i was also just reading up on this just before you posted....what are the chances? :D : [https://ca.godaddy.com/help/install-wordpress-on-your-linux-hosted-domain-using-cpanel-16038](https://ca.godaddy.com/help/install-wordpress-on-your-linux-hosted-domain-using-cpanel-16038)
Hi,

Thanks for your links.

The websites are already running on Godaddy server without problem, not new installation.  I need to download them to my desktop PC.  According to my recollection it was not complicate but need FileZilla to do the job.  My problem is I couldn't recall exactly the steps performed.  I have done multiple times, ten years ago, without problem.  Besides I don't know whether there are new methods after 10 years.

I'll continue searching.  Most of Godaddy documents are out-of-date but they don't update them

satimis

---

### Post by mastablasta on 2018-03-07
you need to dump database to your local server, then you move the files to server.

you might then need to change settings (from goaddy to local) to get it working.

another option is to use a plugin such as urbackup and have it do all (well most of) the work.

---

### Post by satimis on 2018-03-07
> **mastablasta said:**
> you need to dump database to your local server, then you move the files to server.

you might then need to change settings (from goaddy to local) to get it working.

another option is to use a plugin such as urbackup and have it do all (well most of) the work.
Hi,

Thanks for your advice.

The local copy of the website is NOT for Internet browsing.  It serves as a backup of the running websites on Godaddy server.  In case of problem I just upload the local copy back to Godaddy server.  Actually it is only a precaution.  I never use the backup copies before.

satimis

---

### Post by SeijiSensei on 2018-03-07
I've just moved the entire wordpress tree and the MySQL database.  I use mysqldump to create the SQL commands needed to recreate the database.  Transfer the entire tree with rsync or as a tarball, and create the companion MySQL database from the output of the dump.  You'll probably need to make a couple of changes in wp-config.php to point to correct database, etc.

The other option is to use one of the various plugins for this task like [https://wordpress.org/plugins/all-in-one-wp-migration/](https://wordpress.org/plugins/all-in-one-wp-migration/).  (Not an endorsement; I've never used this method.)

---

