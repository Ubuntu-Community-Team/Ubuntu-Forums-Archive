---
title: "ZoneMinder Problem"
date: 2015-07-20
forum: General Help
---

### Post by bmather9 on 2015-07-20
So I've been running my headless server for media/file sharing for a few years now and am quite happy with it.  Recently I decided to add IP cameras to my house and was hoping to use ZoneMinder, but I can't seem to get the software service to run.  I'm pretty confused so I posted in the ZoneMinder forum but no one responded, so I came here hoping someone could help me troubleshoot.  

I followed the installation directions here: [http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_14.04_64-bit_with_Zoneminder_1.28.0_the_easy_way](http://www.zoneminder.com/wiki/index.php/Ubuntu_Server_14.04_64-bit_with_Zoneminder_1.28.0_the_easy_way)

After installation I can access the web interface without problems, but I noticed at the top of the zoneminder web interface it says 'ZoneMinder Console - Stopped v1.28.1'.  I can add a monitor/camera but it stays red and I can stream any video from it.  

I tried to start zoneminder through the web interface and it doesn't work.  On the command line:

```
sudo service zoneminder start
Starting ZoneMinder: failure

sudo service zoneminder status
ZoneMinder is running
```

I'm not sure how it fails to start, but also says it's running??

I also tried to look for a log file in /var/log/zm but there is nothing there. I'm running Ubuntu 14.04.2 LTS GNU/Linux 3.13.0-57-generic x86_64 if that helps. 

Where do I start?

---

### Post by yancek on 2015-07-21
> I'm not sure how it fails to start, but also says it's running??

It can't "start" if it is already running but you might get a positive response if you use "restart", see what happens.

There should be a zoneminder file in the /etc/init.d directory which would have zoneminder start on boot.

>  I can add a monitor/camera but it stays red 

Had this same problem when I installed zoneminder about two years ago and resolved it by adding www-data to the video group and then changing owner:group of /dev/video to www-data:[www.data](www.data)

Easy enough to try.

---

### Post by bmather9 on 2015-07-21
> **yancek said:**
> It can't "start" if it is already running but you might get a positive response if you use "restart", see what happens.

There should be a zoneminder file in the /etc/init.d directory which would have zoneminder start on boot.



Had this same problem when I installed zoneminder about two years ago and resolved it by adding www-data to the video group and then changing owner:group of /dev/video to www-data:[www.data]("http://www.data")

Easy enough to try.

Using the restart actually appears to work in the CLI.  Maybe I'm confused, but when I'm in the web interface, I still see '**ZoneMinder Console - Stopped v1.28.1**'.  When I try to start it via this web interface, it appears to accept the command but remains 'Stopped'.

/dev/video does not exist on my machine; I assume this is used for a local camera which I do not have?  I'm using a Samsung SmartCam IP camera.  

I added a Monitor, using the logic from the follow command which works on this same machine to record from the stream: 

```
avconv -i rtsp://admin:password@192.168.1.105/profile4/media.smp -c copy -map 0 -f segment -segment_time 60 "/rpool/files/media/recording/capture-%03d.mkv"
```

My inputs were:
```
Function>Ffmpeg
Source Path>rtsp://admin:password@192.168.1.105/profile4/media.smp
Remote Method>RTP/RTSP
```
..and nothing more.  

I'm in medium bandwidth mode and the monitor appears in the list but I don't see how I can view the stream? I can't click on the monitor name 'Monitor-1' as there is no link.  The function '[COLOR=#ffa500]Monitor[/COLOR]' is orange and the Source '[COLOR=#ff0000]media.smp[/COLOR]' is red.  

Thanks for the help.  Any ideas?

---

### Post by yancek on 2015-07-21
> but when I'm in the web interface, I still see '**ZoneMinder Console - Stopped v1.28.1**

I don't know why it would do that.  On my install, clicking it changed it to Started or Running.  If you followed the instructions at the link you posted, they explain how to start on boot with the delay for mysql so it should be started when you boot?

> /dev/video does not exist on my machine;

If you looked in the /dev directory for it, no it is not there.  If you look in the file /etc/group, there is a group named video.  According to the link, you need the apache user (www-data) in that group.  Zoneminder uses mysql and Apache and any time you make a change in Apache you need to restart it.

I don't have any other suggestions.  My setup was a built-in webcam on a laptop so that was different than your setup.  Good luck with it.

---

### Post by bmather9 on 2015-07-21
> **yancek said:**
> I don't know why it would do that.  On my install, clicking it changed it to Started or Running.  If you followed the instructions at the link you posted, they explain how to start on boot with the delay for mysql so it should be started when you boot?



If you looked in the /dev directory for it, no it is not there.  If you look in the file /etc/group, there is a group named video.  According to the link, you need the apache user (www-data) in that group.  Zoneminder uses mysql and Apache and any time you make a change in Apache you need to restart it.

I don't have any other suggestions.  My setup was a built-in webcam on a laptop so that was different than your setup.  Good luck with it.

Yes I added the sleep 15 command to delay for mysql start.  

And I had already added the www-data user to the video group.  Apache and the entire system have been restarted, but nothing changed.  

Anyone else out there?

---

