---
title: "Flickr loader/plugin broke"
date: 2014-06-28
forum: General Help
---

### Post by erhollowell on 2014-06-28
After a recent update I now have the condition where my publishing uploader(s) for all my photo software to Flickr will not work. ERROR 403 FORBIDDEN is the message I get from the stand alone uploader while the results on Digicam, Shotwell and Gwenview are much the same.

The stand alone uploader was only installed after the trouble with the Plugins started. I tried uninstall/re-install. On change.

I now don't have a clue. Please could someone give me some help?

---

### Post by cariboo on 2014-06-29
It looks like you have a problem with your account permissions, if you are getting a 403 error. I'd suggest you contact Flickr.

---

### Post by erhollowell on 2014-06-29
> **cariboo907 said:**
> It looks like you have a problem with your account permissions, if you are getting a 403 error. I'd suggest you contact Flickr. 

This may be true. I went to Flickr and deleted my tokens. Then I tried to upload again and got the login request, as would be expected. I did the login and establishhed a new token and then when it went to upload I got the 403 just like before.

The strange thing about this whole deal is Friday it was working just fine. Sometime Saturday it stopped. I figured if Flickr was the problem then there would be alot more noise about it.

---

### Post by takvera on 2014-07-04
From what I have read elsewhere Flickr has updated to using just a secure connection (https), which therefore produces the 403 Forbidden error when the application attempts to log-in using the standard http address. It sounds like this requires a fix in the Flickr Uploader app.

I have just sent an email to the app developer Ross Burton requesting a status update and asking if and when he could update his app.

> Hi Ross,
have appreciated using your Flickr Uploader (0.12.4) app for a number of years running on gnome desktop, now ubuntustudio desktop.

Flickr has now upgraded to secure server connections (https), so when you open the Flickr Uploader app it produces 403 Forbidden errors.

I have read on the Flickr help forum this needs to be resolved through upgrading the App. If it is of any consolation, your app is not the only one that requires an upgrade.
[Official Thread] Flickr API switching to https-only today! (28 June 2014)
[https://www.flickr.com/help/forum/en-us/72157645440333073/](https://www.flickr.com/help/forum/en-us/72157645440333073/)

This error has been reported on the Ubuntu forum here:
[http://ubuntuforums.org/showthread.php?t=2231929&highlight=flickr+uploader](http://ubuntuforums.org/showthread.php?t=2231929&highlight=flickr+uploader)

let us know via the forum the status of your app and whether you will upgrade it using the secure API.

regards

---

### Post by takvera on 2014-07-04
Just got a response via twitter from Ross Burton:

>  sorry, I haven't maintained that for several years now.- Ross Burton (@rossburton) 
[https://twitter.com/rossburton/statuses/484958023090462720](https://twitter.com/rossburton/statuses/484958023090462720)
July 4, 2014

So it looks like we might be searching for another Flickr app that can deal with https connection. Any ideas?

---

### Post by takvera on 2014-07-05
Just received a reply from the person who has taken over maintenaince of Flickr Uploader app called postr:
> Hi,
I just releases 0.12.5 and 0.13.1 with the problem fixed.
Both of them are stable, though 0.13 series is newer than 0.12 one.
Regards,
--
Germán Poo-Caamaño
[http://calcifer.org/](http://calcifer.org/)

so the main ubuntu app repository needs to be updated with latest version. 
Don't know how to get that happening. Ideas anyone?

---

### Post by erhollowell on 2014-07-27
Thanks for the responses all. The last install of Ubuntu I did included F-spot which seemed to have the plugin left out. The older instals at least get the 403 message but the last one gives no response at all to the publish request. I have about 400 photos to upload and resize and it sucks doing it manually. At least now I know it's not just me.

---

