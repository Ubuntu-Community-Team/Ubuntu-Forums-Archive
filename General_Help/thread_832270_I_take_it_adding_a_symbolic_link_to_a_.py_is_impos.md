---
title: "I take it adding a symbolic link to a .py is impossible?"
date: 2008-06-17
forum: General Help
---

### Post by Majin_Buu on 2008-06-17
I just instaleld sabnzbd+ on my linux setup. I tried creating a symbolic link but I ended up with so many errors I had to resort back to my home folder everytime I launch the script.

So I take it the only way I will run this program is within its native (installed) path?

```
greenfish@skynet:/usr/local/bin$ sudo ln -s /usr/share/apps/SABnzbd-0.4.0RC2/SABnzbd.py /usr/local/bin/sab
greenfish@skynet:/usr/local/bin$ ls
sab
greenfish@skynet:/usr/local/bin$ file sab
sab: symbolic link to `/usr/share/apps/SABnzbd-0.4.0RC2/SABnzbd.py'
greenfish@skynet:/usr/local/bin$       
 
 
 
2008-06-17 21:21:14,636::INFO::--------------------------------
2008-06-17 21:21:14,638::INFO::sab-0.4.0RC2 (rev=1180)
2008-06-17 21:21:14,639::INFO::Platform = posix
2008-06-17 21:21:14,640::INFO::Python-version = 2.5.2 (r252:60911, Apr 21 2008, 11:12:42)
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)]
2008-06-17 21:21:14,641::INFO::Test release, setting maximum logging levels
2008-06-17 21:21:14,642::DEBUG::auto_browser -> 1
2008-06-17 21:21:14,643::DEBUG::permissions ->
2008-06-17 21:21:14,644::DEBUG::username ->
2008-06-17 21:21:14,645::DEBUG::password -> ******
2008-06-17 21:21:14,646::DEBUG::check_new_rel -> 1
2008-06-17 21:21:14,647::DEBUG::replace_spaces -> 0
2008-06-17 21:21:14,648::DEBUG::fail_on_crc -> 0
2008-06-17 21:21:14,649::DEBUG::enable_filejoin -> 0
2008-06-17 21:21:14,650::DEBUG::enable_unzip -> 1
2008-06-17 21:21:14,652::DEBUG::enable_unrar -> 1
2008-06-17 21:21:14,653::DEBUG::enable_save -> 1
2008-06-17 21:21:14,654::DEBUG::enable_par_cleanup -> 1
2008-06-17 21:21:14,655::DEBUG::config_lock -> 0
2008-06-17 21:21:14,656::DEBUG::safe_postproc -> 0
2008-06-17 21:21:14,657::DEBUG::pause_on_post_processing -> 0
2008-06-17 21:21:14,658::DEBUG::cleanup_list -> []
2008-06-17 21:21:14,659::DEBUG::ignore_samples -> 0
2008-06-17 21:21:14,660::DEBUG::permissions ->
2008-06-17 21:21:14,661::DEBUG::send_group -> 0
2008-06-17 21:21:14,662::DEBUG::bookmarks -> 0
2008-06-17 21:21:14,663::DEBUG::unbookmark -> 0
2008-06-17 21:21:14,664::DEBUG::bookmark_rate -> 60
2008-06-17 21:21:14,665::DEBUG::download_dir: /home/greenfish/downloads/incomplete
2008-06-17 21:21:14,666::DEBUG::download_free -> 0
2008-06-17 21:21:14,667::DEBUG::DOWNLOAD_FREE 0
2008-06-17 21:21:14,668::DEBUG::complete_dir: /home/greenfish/downloads/complete
2008-06-17 21:21:14,670::DEBUG::cache_dir: /home/greenfish/.sabnzbd/cache
2008-06-17 21:21:14,671::DEBUG::dirscan_speed -> 5
2008-06-17 21:21:14,672::DEBUG::refresh_rate -> 0
2008-06-17 21:21:14,673::DEBUG::rss_rate -> 60
2008-06-17 21:21:14,675::DEBUG::bandwith_limit -> 0
2008-06-17 21:21:14,676::DEBUG::cache_limit -> 0
2008-06-17 21:21:14,677::DEBUG::Actual cache limit = 0
2008-06-17 21:21:14,680::DEBUG::email_server ->
2008-06-17 21:21:14,683::DEBUG::email_to ->
2008-06-17 21:21:14,684::DEBUG::email_from ->
2008-06-17 21:21:14,684::DEBUG::email_account ->
2008-06-17 21:21:14,685::DEBUG::email_pwd -> ******
2008-06-17 21:21:14,686::DEBUG::email_endjob -> 0
2008-06-17 21:21:14,686::DEBUG::email_full -> 0
2008-06-17 21:21:14,687::DEBUG::dirscan_opts -> 3
2008-06-17 21:21:14,688::DEBUG::dirscan_script ->
2008-06-17 21:21:14,688::DEBUG::top_only -> 1
2008-06-17 21:21:14,689::DEBUG::auto_sort -> 0
2008-06-17 21:21:14,690::DEBUG::enable_tv_sorting -> 0
2008-06-17 21:21:14,690::DEBUG::tv_sort_string ->
2008-06-17 21:21:14,691::DEBUG::web_color ->
2008-06-17 21:21:14,691::DEBUG::web_color2 ->
2008-06-17 21:21:14,692::INFO::[sabnzbd] Loading data for rss_data.sab from /home/greenfish/.sabnzbd/cache/rss_data.sab
2008-06-17 21:21:14,693::DEBUG::Scheduling VersionCheck day=(3,) time=3:29
2008-06-17 21:21:14,694::INFO::[sabnzbd] Loading data for bytes7.sab from /home/greenfish/.sabnzbd/cache/bytes7.sab
2008-06-17 21:21:14,695::INFO::[sabnzbd] Loading data for queue7.sab from /home/greenfish/.sabnzbd/cache/queue7.sab
2008-06-17 21:21:14,698::INFO::_yenc module... found!
2008-06-17 21:21:14,702::INFO::celementtree module... found!
2008-06-17 21:21:14,703::INFO::par2 binary... found (/usr/bin/par2)
2008-06-17 21:21:14,703::INFO::rar binary... found (/usr/bin/unrar)
2008-06-17 21:21:14,704::INFO::unzip binary... found (/usr/bin/unzip)
2008-06-17 21:21:14,704::INFO::pyOpenSSL... NOT found - try apt-get install python-pyopenssl (SSL is optional)
2008-06-17 21:21:14,705::DEBUG::host -> localhost
2008-06-17 21:21:14,707::DEBUG::port -> 8080
2008-06-17 21:21:14,708::DEBUG::log_dir: /home/greenfish/.sabnzbd/logs
2008-06-17 21:21:14,709::INFO::Web dir is /usr/local/bin/interfaces/Plush
2008-06-17 21:21:14,710::WARNING::Cannot find web template: /usr/local/bin/interfaces/Plush/templates/main.tmpl, trying standard template
2008-06-17 21:21:14,710::ERROR::Cannot find standard template: /usr/local/bin/interfaces/Default
Traceback (most recent call last):
  File "/usr/local/bin/sab", line 63, in <module>
    import win32api
ImportError: No module named win32api
```

---

### Post by geirha on 2008-06-17
It's perfectly possible to have a symbolic link to a python app, just not in the case of the application you are using here, since it expects a folder called interfaces to be in the same folder as the executable (or symbolic link in this case).

Instead of making a symlink, you can make a small script that you save as /usr/local/bin/sap, and make executable:
```
$ gedit /tmp/sap
```
[php]
#!/bin/bash
cd /usr/share/apps/SABnzbd-0.4.0RC2/
exec ./SABnzbd.py
[/php]
```
$ chmod +x /tmp/sap
$ sudo mv /tmp/sap /usr/local/bin/sap

```

---

### Post by Majin_Buu on 2008-06-18
:popcorn:> **geirha said:**
> It's perfectly possible to have a symbolic link to a python app, just not in the case of the application you are using here, since it expects a folder called interfaces to be in the same folder as the executable (or symbolic link in this case).

Instead of making a symlink, you can make a small script that you save as /usr/local/bin/sap, and make executable:
```
$ gedit /tmp/sap
```
[php]
#!/bin/bash
cd /usr/share/apps/SABnzbd-0.4.0RC2/
exec ./SABnzbd.py
[/php]
```
$ chmod +x /tmp/sap
$ sudo mv /tmp/sap /usr/local/bin/sap

```

holy friggin moses it worked :popcorn: :popcorn:


THANKS A LOT BUDDY :)

Tell me how did you know the python scripted required "interfaces"?

Also do you have any good links I can read on understand these type of things, I really want to learn.

what is /tmp/sap?

Thanks again man 

btw I added -d after .py in the script, starts the service as "daemon" wow  :lolflag:

---

### Post by geirha on 2008-06-18
> **Majin_Buu said:**
> 
Tell me how did you know the python scripted required "interfaces"?

Educated guess. The following three lines indicated that it was trying to access data files in /usr/local/bin/interfaces/. Your average linux application would never do such a thing, so the logical assumption would be that this application was written in a "windows"-style (in lack of a better word) where all files relating to an application is located at the same place and not spread around the filesystem as it is in ubuntu. 
```

2008-06-17 21:21:14,709::INFO::Web dir is /usr/local/bin/interfaces/Plush
2008-06-17 21:21:14,710::WARNING::Cannot find web template: /usr/local/bin/interfaces/Plush/templates/main.tmpl, trying standard template
2008-06-17 21:21:14,710::ERROR::Cannot find standard template: /usr/local/bin/interfaces/Default

```
It was a good call pasting the full output of the command. Since I had never heard of that application before, I wouldn't have guessed the problem otherwise.

> **Majin_Buu said:**
> 
Also do you have any good links I can read on understand these type of things, I really want to learn.

«these type of things» is a large range of subjects, and I wouldn't know what to start you off with really. Someone else at these forums might have some pointers on that, and google is a nice place to find tutorials and guides regarding most subjects.

> **Majin_Buu said:**
> 
what is /tmp/sap?


We needed to create a script, and /tmp/ is a special directory where all users have write access, so creating a file called sap there should be a fairly safe bet (unless there was a file with that name there allready, which is unlikely). And so we could create and change the file without using sudo, but /usr/local/bin/ is only writable by root, so to move (mv) the script there, sudo was needed.

> **Majin_Buu said:**
> 
btw I added -d after .py in the script, starts the service as "daemon" wow  :lolflag:

If you need it to run as a daemon, then that's a good idea. To get the same result, you could also change '-d' with '$1', and then if you run «sap -d», the $1 will be replaced by the -d you typed after sap. (And if you ran «sap» without the -d, $1 would be replaced with '' a.k.a. nothing.

---

### Post by Majin_Buu on 2008-06-20
> **geirha said:**
> Educated guess. The following three lines indicated that it was trying to access data files in /usr/local/bin/interfaces/. Your average linux application would never do such a thing, so the logical assumption would be that this application was written in a "windows"-style (in lack of a better word) where all files relating to an application is located at the same place and not spread around the filesystem as it is in ubuntu. 
```

2008-06-17 21:21:14,709::INFO::Web dir is /usr/local/bin/interfaces/Plush
2008-06-17 21:21:14,710::WARNING::Cannot find web template: /usr/local/bin/interfaces/Plush/templates/main.tmpl, trying standard template
2008-06-17 21:21:14,710::ERROR::Cannot find standard template: /usr/local/bin/interfaces/Default

```
It was a good call pasting the full output of the command. Since I had never heard of that application before, I wouldn't have guessed the problem otherwise.


«these type of things» is a large range of subjects, and I wouldn't know what to start you off with really. Someone else at these forums might have some pointers on that, and google is a nice place to find tutorials and guides regarding most subjects.



We needed to create a script, and /tmp/ is a special directory where all users have write access, so creating a file called sap there should be a fairly safe bet (unless there was a file with that name there allready, which is unlikely). And so we could create and change the file without using sudo, but /usr/local/bin/ is only writable by root, so to move (mv) the script there, sudo was needed.



If you need it to run as a daemon, then that's a good idea. To get the same result, you could also change '-d' with '$1', and then if you run «sap -d», the $1 will be replaced by the -d you typed after sap. (And if you ran «sap» without the -d, $1 would be replaced with '' a.k.a. nothing.

thanks again for your explanation, I will try my best and borrow linux books, bibles etc and try to learn the system from scratch sort of. I realise it's not easy to choose what path one must take in order to understand a certain function in linux, it's probably better to start at scratch, ergo the foundation.

Here's a part I dont understand:

> Educated guess. The following three lines indicated that it was trying to access data files in /usr/local/bin/interfaces/. Your average linux application would never do such a thing, so the logical assumption would be that this application was written in a "windows"-style (in lack of a better word) where all files relating to an application is located at the same place and not spread around the filesystem as it is in ubuntu. 

You said windows likes to run everything off its native source but linux doesnt. But how come its trying to access /usr/local/bin/interfaces then? Isnt that what it should be doing in the first place, like you said "spread around the fiesystem as it is in ubuntu" ?

your script is working great, thanks again man :)

---

### Post by geirha on 2008-06-20
> **Majin_Buu said:**
> 
You said windows likes to run everything off its native source but linux doesnt. But how come its trying to access /usr/local/bin/interfaces then? Isnt that what it should be doing in the first place, like you said "spread around the fiesystem as it is in ubuntu" ?

your script is working great, thanks again man :)

Yes, your binary was in /usr/local/bin/, so it tried to find its datafiles in the same place, that's common in the windows world. In linux, you'd look for those files in /usr/local/share/progname/, /usr/local/lib, /var/lib/progname/ and so forth.

---

### Post by Majin_Buu on 2008-06-20
> **geirha said:**
> Yes, your binary was in /usr/local/bin/, so it tried to find its datafiles in the same place, that's common in the windows world. In linux, you'd look for those files in /usr/local/share/progname/, /usr/local/lib, /var/lib/progname/ and so forth.

ah I understand, thank you :popcorn:

---

