---
title: "Setup remote desktop on Android phone to be navigated on Ubuntu 22.04 PC via WiFi"
date: 2023-05-08
forum: General Help
---

### Post by satimis on 2023-05-08
[COLOR="#FF0000"]Setup remote desktop on Android phone to be navigated on Ubuntu 22.04 PC via WiFi[/COLOR]

Hi all,

Please advise where can I find tutorial to set up remote desktop on Samsung Galaxy S9+ phone (Android phone) to be remotely navigated via WiFi on the screen of Ubuntu 22.04 PC for photo-shooting.  I have done it before.  It worked seamlessly.

The screen of the Android phone was remotely displayed on the screen of Ubuntu 22.04 PC. I just clicked the shooting button with mouse pointer then it captured the photo.  The photos were stored on the Android phone.  I have to manually download them to Ubuntu 22.04 PC.

Unfortunately I forgot the steps, unable to locate its file saved on my database.

Please help.  Thanks

Regards

---

### Post by satimis on 2023-05-08
Hi all,

Further to my OP above, an interesting discovery was found on Google searching;

**[COLOR="#FF0000"][Can't Miss] How to Cast to A Browser from Mobile?[/COLOR]**
[https://www.airdroid.com/screen-mirror/cast-to-browser/](https://www.airdroid.com/screen-mirror/cast-to-browser/)

Has any folk on the forum tried it ?  Please shed me some light.  Thanks

This is very convenient, saving efforts to install and setup software on both Android phone and Ubuntu 22.04 desktop.  According to my weak recollection I used TeamViewer in the past to connect Android phone to Ubuntu 22.04 desktop.  I don't have SIM card installed on my Android phone.  I only have WiFi connection.

Regards

---

### Post by TheFu on 2023-05-08
GSconnect or KDEConnect are probably what you seek.
[https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect)
[https://kdeconnect.kde.org/](https://kdeconnect.kde.org/)

There are other options too with fewer dependencies, no GUI, hence lighter.  Whether any of these tools works with any specific android device or not is something I don't know.  I use other methods and haven't setup anything with my new-to-me (phone and tablet) purchased in the last 6 months.

I never understand why people would put a 3rd party between their 2 devices. Seems crazy to me.

---

### Post by satimis on 2023-05-08
> **TheFu said:**
> GSconnect or KDEConnect are probably what you seek.
[https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect)
[https://kdeconnect.kde.org/](https://kdeconnect.kde.org/)

There are other options too with fewer dependencies, no GUI, hence lighter.  Whether any of these tools works with any specific android device or not is something I don't know.  I use other methods and haven't setup anything with my new-to-me (phone and tablet) purchased in the last 6 months.

I never understand why people would put a 3rd party between their 2 devices. Seems crazy to me.

Hi TheFu,

Thanks for your advice and link.

What I'm prepared to do is scanning hundreds of old photos to digial.  It is very convenient and efficient taking a shot on camera instead of scanning the old photos on scanner.  I did it before, quite sometime ago but not finish yet.

Now I have time and need to continue the work.  Unfortunately I forgot its setup up.  

The past setup was as follows;
1. Mount the Android phone, the camera, on a tripod above an indexing table
2. Connect the Android phone to Ubuntun 22.04 PC via WiFi
3. Place the old photo on the indexing table
4. Click the start button of the Android phone camera on the screen of Ubuntu 22.04 PC to shoot
5. Place another old photo on the indexing and repeat the step 4 above.

I need a simple setup to connect the Android phone to Ubuntu 22.04 PC to contiue my unfinished job.  Do you have any suggestion?

On Internet searching I found following video;
How to remotely access android phone on Ubuntu
[https://www.youtube.com/watch?v=OLtauh6UHkQ](https://www.youtube.com/watch?v=OLtauh6UHkQ)

It needs connecting the Android phone to Ubuntu PC via an USB cable.

Do you have another idea?  Or any folk on the forum has a suggestion?

Thanks in advance

Regards

---

### Post by satimis on 2023-05-09
Hi all,

Just tried the version suggested on following video;

**[COLOR="#FF0000"]How to remotely access android phone on Ubuntu[/COLOR]**
[https://www.youtube.com/watch?v=OLtauh6UHkQ](https://www.youtube.com/watch?v=OLtauh6UHkQ)

It works seamlessly to remote control the Android phone (in my case - Samsung Galaxy S9+ an old smart phone)

**[COLOR="#FF0000"]Steps performed as follows;[/COLOR]**
1. Connect the Android phone to Ubuntu 22.04 PC with an USB cable
2. Following the steps on the video to configure the Android phone and to enable USB debugging.
3. Install "scrcpy" on Ubuntu 22.04 PC.  "scrcpy" is on repo
4. On terminal start "scrcpy".  Failed and it can't connect the server.
5. On terminal run "adb kill-server"
6. Start "scrcpy" again.

This time it works displaying the Android phone screen on the display of Ubuntu 22.04 PC.  I can remote-shoot photos with the Android phone camera on the display of Ubuntu PC.

The only draw-back is needing to connect the Android phone with an USB cable.  I'm still searching the method via WiFi connection.

Please refers to attached screenshot

Regards

---

### Post by satimis on 2023-05-10
Hi all,

Now problem have been completely solved.

Follow the steps on below YouTube video
**[COLOR="#FF0000"]How to debug Android application over WIFI(Without USB cable)[/COLOR]**
[https://ihilalahmadd.medium.com/how-to-debug-android-application-over-wifi-without-usb-cable-d29927891614](https://ihilalahmadd.medium.com/how-to-debug-android-application-over-wifi-without-usb-cable-d29927891614)

Now I can remotely navigate the Android phone on Ubuntu 22.04 PC, seamlessly.
[B][COLOR="#FF0000"]
Wonderful !!!!![/COLOR][/B]

I believe that in the past I didn't work on this route

Regards

---

