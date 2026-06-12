---
title: "Gnump3d: Movies can't be found"
date: 2007-07-16
forum: General Help
---

### Post by SGulseth on 2007-07-16
Hey

I have Gnump3d server installed on my Ubuntu Linux, Feisty Fawn 7.04,  and streaming music to my laptop all day. But when I try to stream a movie/video i get a 404 error. 
eks, trying to stream "Justin_Timberlake_-_My_Love.avi":
> **Firefox]
The requested file /var/media/Musikk/Justin_Timberlake_-_My_Love.avi couldn't be found. Please try returning to the index.
[/quote]
[quote=tail access.log]
88.91.148.24 - - [17/Jul/2007:01:10:22 +0000] "GET /Musikk/Eminem_-_Like_toy_soldiers_(produced_by_eminem)-rns.mp3" 410 2862060 "-" "Mozilla/5.0 (X11 said:**
>  "GET /Musikk/05-talib_kweli-ms._hill-c4.mp3.m3u" 200 967 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
88.91.148.24 - - [17/Jul/2007:01:10:25 +0000] "GET /Musikk/05-talib_kweli-ms._hill-c4.mp3" 200 5389261 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
88.91.148.24 - - [17/Jul/2007:01:10:31 +0000] "GET /Musikk/Jay-Z - Encore.mp3.m3u" 200 959 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
88.91.148.24 - - [17/Jul/2007:01:10:33 +0000] "GET /Musikk/Jay-Z - Encore.mp3" 410 2153452 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
88.91.148.24 - - [17/Jul/2007:01:10:38 +0000] "GET /Musikk/Usher & Jadakiss - Burn (Remix).mp3.m3u" 200 988 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
88.91.148.24 - - [17/Jul/2007:01:10:40 +0000] "GET /Musikk/Usher & Jadakiss - Burn (Remix).mp3" 200 6094155 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
88.91.148.24 - - [17/Jul/2007:01:10:48 +0000] "GET /Musikk/Usher - Yeah ft. Lil Jon & Ludacris.mp3.m3u" 200 992 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
88.91.148.24 - - [17/Jul/2007:01:10:51 +0000] "GET /Musikk/Usher - Yeah ft. Lil Jon & Ludacris.mp3" 200 5972972 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"
88.91.148.24 - - [17/Jul/2007:01:10:54 +0000] "GET /var/media/Musikk/Justin_Timberlake_-_My_Love.avi" 404 3700 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)"


[quote=tail -16 error.log]
Header: HTTP/1.0 404 OK
Connection: close
Server: GNUMP3d 2.9.9.1
Content-type: text/html
Set-Cookie: album=;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: arcticgaming_login=425|test|abe45d28281cfa2a4201c9b90a143095;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: artist=;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: count=50;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: dir=;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: genre=;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: submit=Try Again;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: theme=Tabular;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: title=;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: type=all;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
Set-Cookie: year=;path=/; expires=Mon, 10-Mar-08 14:36:42 GMT;
[/quote]

Edit: I found out why I get a 404 error: The real path to the video are /Musikk/Justin_Timberlake_-_My_Love.avi and not /var/media/Musikk/Justin_Timberlake_-_My_Love.avi. It looks like it prints out differents links when it is a video.

Now the problem is: how to fix this? :)

---

### Post by sunra350 on 2007-08-07
see my post I resolved the issue.

[http://ubuntuforums.org/showthread.php?t=518838&highlight=gnump3d](http://ubuntuforums.org/showthread.php?t=518838&highlight=gnump3d)

---

