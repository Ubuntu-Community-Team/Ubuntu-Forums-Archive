---
title: "Transmission unable to find data on startup"
date: 2014-09-24
forum: General Help
---

### Post by howeishotweb on 2014-09-24
Hello,

I am having trouble getting the Transmission torrent client to start up with my computer and resume my torrents.
I have added transmission-gtk to my startup programs, but the status for all torrents is that it is unable to find the data.
I have then made the hard-drive holding the data to auto-mount on startup, thinking that was the issue, but it didn't help.

I have also tried editing the startup file for Transmission to add a delay before starting, but after doing that it's like Transmission gets removed from the auto-startup list, and it doesn't start up at all.

When I click Resume to the torrents, they resume and work completely fine.

Any help would be appreciated.

---

### Post by ian-weisser on 2014-09-24
From your description, seems likely to be permissions. The daemon cannot access the data without your help.

Transmission-daemon is the actual always-on torrent-client service that you want running. You generally want it to run at startup (not login) after the network interfaces and mounted disks become available. Check /etc/init for the upstart job that starts the service. The service (not the Upstart job) needs access to your torrent files and data. It often runs as a different user than you, so make sure _it_ can read/write those files.

The gtk interface (or web interface or CLI interface) is what you use to talk to the service. This can only be started by you (the user) after login because it requires access to your display. The interface application should not require a delay - login only occurs after network and disks are available anyway. If the daemon is not available, the interface will give you a proper error.

---

### Post by howeishotweb on 2014-09-26
Thank you for your reply.

I do not immediately see anything in /etc/init related to Transmission, though I'm not sure what I'm looking after.

I tried replacing transmission-gtk with transmission-daemon in the Startup Applications program, but then nothing starts up.
If you could give a quick guide for what to do, that would be great.

---

### Post by ian-weisser on 2014-09-27
> **victorfhansen said:**
> I tried replacing transmission-gtk with transmission-daemon in the Startup Applications program

That won't work. transmission-gtk was correct, if you want the user interface to start at login.
And that's not the problem you described anyway. You described a permission problem, not a wrong-application problem.

Did you install Transmission from the Ubuntu repositories? Or did you get if from someplace else? (where?)

Who owns the torrent files and data files that you want transmission to use?

Here's an example of mine. I start transmission-daemon at boot, and run it headless
```
$ ls -l transmission_downloads/example_file
-rw-r--r-- 1 debian-transmission debian-transmission 32654 Sep 21 20:25 transmission_downloads/example_file
```

See how the file is not owned by me? It's owned by a user called 'debian-transmission'
If the file is owned by me instead of debian-transmission, the transmission daemon will fail to load it. That's an example of a permission error: The debian-transmission user does not have permission to go mucking through my files.
And it's really easy to fix, _if_ that's your problem.

---

### Post by howeishotweb on 2014-09-29
I am not sure it is a permission problem anymore. Now, sometimes all the torrents are seeding fine on startup, other times they give the "Data not found" error message. The newest torrent I have added never fails to seed, though. The data for this torrent is placed on another drive.

I would like to try adding a delay to Transmission, to see if that would fix it.

---

### Post by nerdtron on 2014-09-29
> **victorfhansen said:**
> I am not sure it is a permission problem anymore. Now, sometimes all the torrents are seeding fine on startup, other times they give the "Data not found" error message. The newest torrent I have added never fails to seed, though. The data for this torrent is placed on another drive.

I would like to try adding a delay to Transmission, to see if that would fix it.

I really think this is a permission issue. What is the location of the mount point of the other hard drive where you save the torrents?

```
cd /mnt/path/to/folder
ls -lah
```

---

### Post by ian-weisser on 2014-09-29
> **victorfhansen said:**
> I am not sure it is a permission problem anymore. Now, sometimes all the torrents are seeding fine on startup, other times they give the "Data not found" error message. The newest torrent I have added never fails to seed, though. The data for this torrent is placed on another drive.

Nerdtron is right.
"Data not found" smells *exactly* like a permission issue. If the daemon cannot read the file, it will return a 'not found' error.
A delay won't help. The filesystem is mounted and stable (and the network is up) before the torrent daemon starts anyway.

It could be worse. An intermittent 'data not found' error when you are starting *exactly* the same way each time could mean corrupted data or a failing drive.

---

### Post by howeishotweb on 2014-10-02
Hmm, you're probably right. I have now added more torrents, and it is only torrents I put on Disk 1 that have issues.
An example from ls -lah of a folder containing some torrents:

> drwxrwxrwx  5 victor victor 4,0K Aug 31 20:28 Mobile Suit Gundam MS IGLOO


Mount point for Disk 1: > /media/victor/Anime$

Mount point for Disk 2(the one without problems): > /media/victor/Music$

No dfferent there... There was problems with me not owning those disks after formatting them, I used chown to get access to them. Maybe something went wrong there?

---

### Post by ian-weisser on 2014-10-03
> **victorfhansen said:**
> There was problems with me not owning those disks after formatting them, I used chown to get access to them.

I think you have properly diagnosed the problem.
If so, be sure to mark thread 'Solved' using the Thread Tools at the top of this page.

---

### Post by howeishotweb on 2014-10-03
Uh... Okay... I might have misunderstood something, but a solution would be nice too... The chown thing was some time ago, when I formatted the disks from NTFS to ext4.

---

### Post by ian-weisser on 2014-10-03
Now I am confused.
Are you saying that changing the ownership (chowning) was not the solution?

Remember, the Transmission daemon does not run under your username. The daemon's user must be able to access the disk.

---

### Post by howeishotweb on 2014-10-04
I haven't changed anything yet. What do I need to do to give Transmission access?

---

### Post by nerdtron on 2014-10-04
```
sudo chmod -R 777 /path/to/saved/folder
```

It's easy this way instead on using chown as you have transmission and you have your username, your even have root. If you don't mind your files being world readable/writable just like an ntfs partition, might as well shotgun it with 777.

---

