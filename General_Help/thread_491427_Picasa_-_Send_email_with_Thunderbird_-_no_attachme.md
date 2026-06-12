---
title: "Picasa - Send email with Thunderbird - no attachments"
date: 2007-07-03
forum: General Help
---

### Post by MCSE_Crossover on 2007-07-03
Has anyone had any luck any luck getting Picasa to successfully send an email using Thunderbird? I can hit "email" within Picasa and have it open Thunderbird, but it doesn't attach any of the pictures that I have selected. I know this is touched on in Google's Picasa FAQ, but wondering if there is a work around.

[http://picasa.google.com/linux/faq.html#13](http://picasa.google.com/linux/faq.html#13)

Anyone know how to edit the picasa-email-hook.sh file to properly support this?

Gracias Amigos! You're all the bomb!

---

### Post by MCSE_Crossover on 2007-07-06
bump? No one ever tries to send emails with thunderbird through Picasa?

---

### Post by Beernut on 2007-07-21
Good Luck.  I have been looking for the same thing.  I am trying to get my wife to switch from Windows and this is a big complaint of hers.  In Windows all she has to do is select the photos right click and select email photos.  Works with Thunderbird no problems.  I have recently tried several Nautilus scripts that don't work well especially sending with Thunderbird and can't find one that does both resize the image and send by email all in one script.  Seems to me that there is something wrong with Thunderbird that makes this difficult.

---

### Post by MCSE_Crossover on 2007-07-22
Yeah, i'm not sure. I actually just installed KDE instead and am now using Digikam. It is the closest variant to that of Picasa and Digikam works with sending emails with Thunderbird...so does F-Spot for the record. But, I think Digikam is a superior program than F-Spot. The Picasa linux doesn't provide the web albums upload feature either, so really, it is pointless to use at this point. Have you wife try Digikam. Although I don't think it is as superior as Picasa as far as ease of use, it is still a nice program.

Now if I could just get Firefox/Thunderbird to display image previews when browsing, we would be all set!

---

### Post by Beernut on 2007-07-22
I am starting to think Kubuntu might be a better choice for the family computer.  I am downloading the ISO now and will be giving it a try.  You might want to check out [KIPI Plugins]("http://www.kipi-plugins.org/drupal/?q=node/1") if you haven't already.

---

### Post by MCSE_Crossover on 2007-07-23
Yeah, I moved over to Kubuntu myself. To me, there just really isn't any reason to stay on Ubuntu...KDE just seems to have all the best apps. K3B, ktorrent, digikam...those three alone are the only one's that I really use and all are far superior to the Gnome apps.

It is just so frustrating that things you would think would just "work" dont...I have to find all these stupid work arounds for everything. Where I gain a feature going one direction, I lose a feature as well.

Such is the case with this Thunderbird/Picasa/Digikam/F-Spot thing.

I think that Picasa is superior to Digikam and F-Spot in ease of use and features, But I can't send an email through Thunderbird because it doesn't attach the friggin' pictures. F-Spot is superior to Picasa and Digikam becauase you can export to PicasaWeb, Flickr, Gallery, etc. Picasa Linux doesn't have the feature and Digikam only exports to Flickr. THEN, if I used Evolution or Kmail, Picasa would email fine, but then I lose the functionality of Thunderbird's "profile manager" and I don't want to set up multipe user names because the Picasa won't share the database the right way. Kmail or Evolution would be great if they had a similar "profile manager" feature of Thunderbird...but they don't. So the only one's that use the computer are my wife and I. I have no need to set up to user names. And when she add's pictures to the computer, I want it in the same folder structure and I want all the changes made to reflect the same. How do I do that under two seperate users? 

It is all so STUPID and FRUSTRATING. Flame me all you want, but this is where Windows and Mac just WORK. Hate to say it, but it's true. Linux is work around after work around...man, what a pain in my ****.

There is my short rant...sooner or later i'm going to post a long one in the main forum. :)

---

### Post by Re Persina on 2007-12-26
Sorry for replying to such an old thread but this happens to be the top result right now when googling for picasa-thunderbird email issues. (use the View Full Version link at the top if you're viewing the text-only archive version)

Using Picasa on Linux and emailing pictures via Thunderbird does not work correctly (subject, message text and/or attachment are missing), but making use of the picasa-email-hook.sh file can probably solve your problems. (I assume you are using Picasa 2.7 Beta version. I haven't tested other versions. Get the latest version here: [http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html))

The attached script, saved as: **/opt/picasa/bin/picasa-hook-email.sh** should allow emails from Picasa to work correctly with Thunderbird. Note, I did not create this script! It was graciously provided by someone posting to the Google-Picasa for Linux group. I only attached it here to make it easier to use because the version posted to the group must be edited due to wrapped lines.
original source: [http://groups.google.com/group/Google-Labs-Picasa-for-Linux/msg/95be40a83da27a75](http://groups.google.com/group/Google-Labs-Picasa-for-Linux/msg/95be40a83da27a75)

Detailed instructions for those who need them:
1) Exit Picasa if it is open (Stop the Picasa media detector as well)
2) Save the attached script to your home directory, or somewhere. 
3) Open a terminal window
4) Use sudo to move the script to the proper location:
```
sudo mv picasa-hook-email.sh /opt/picasa/bin/
```
5) Make the script executable: 
```
sudo chmod 755 /opt/picasa/bin/picasa-hook-email.sh
```

That's it! Emails from Picasa using Thunderbird should now work as expected.

---

### Post by ebioman on 2007-12-28
Works fine, thanks !!

---

