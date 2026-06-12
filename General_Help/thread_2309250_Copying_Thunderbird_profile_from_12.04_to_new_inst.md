---
title: "Copying Thunderbird profile from 12.04 to new installation of 14.04"
date: 2016-01-08
forum: General Help
---

### Post by Angela_C.Murphy on 2016-01-08
I have 12.04 and 14.04 on different partitions.  I would like to copy my Thunderbird settings from 12.04.

I have read that the way to do this is to back up the hidden file .thunderbird to a USB Flash Drive and then boot into 14.04, and use restore to substitute the 12.04 .thunderbird for the 14.04 .thunderbird (which is presently empty).

Is that the best way to copy the settings?  Is there any easier way to do it?

Thanks for any help on this.
Angela C. Murphy

---

### Post by Bucky Ball on 2016-01-08
That is the best and easiest way to do it (and unaware of any other way to do it). You can simply copy it to the 14.04 folder while booted into 12.04 if you can find it (mount the 14.04 partition and navigate to the user there, delete .thunderbird and copy the 12.04 .thunderbird in to that folder). Or, copy to external device as you describe. Not sure how it could get much easier. :)

Delete the empty .thunderbird in the new 14.04 install then plop in the 12.04 copy. Reboot or simply start Thunderbird (which shouldn't be launched while you're doing this, naturally).

---

### Post by kurt18947 on 2016-01-08
There is another method. There is an extension called ImportExportTools. For whatever reason, when i check Thunderbird -> Tools -> Add-Ons, it doesn't show up.  If I google "thunderbird import export" it shows up, no idea why it doesn't appear in Add-Ons. Here's a link:

[https://addons.mozilla.org/en-us/thunderbird/addon/importexporttools](https://addons.mozilla.org/en-us/thunderbird/addon/importexporttools)

I've used it with good success, there are a few different options. There was a poster that didn't have as good luck with it but it has done what I've expected of it.

Edit: I tried to install this extension just now on a fresh Thunderbird install. If I clicked the first option The extension was attached to a new email message. I did the manual method - download and use the button to the left of the extension search box and that worked. ImportExport tools appears at the bottom of the 'tools' menu.

---

### Post by Irihapeti on 2016-01-09
ImportExport Tools is for email messages only. It won't transfer address books, email accounts, message filters and other settings.

The method Bucky Ball mentions is the one I've used for the past 9 years that I've been using Thunderbird.

---

### Post by howefield on 2016-01-09
If you have a common partition that both Ubuntu installations can access, another option might be to share a single profile, making it easier to maintain and backup.

Just another method :)

---

### Post by kurt18947 on 2016-01-09
> **Irihapeti said:**
> ImportExport Tools is for email messages only. It won't transfer address books, email accounts, message filters and other settings.

The method Bucky Ball mentions is the one I've used for the past 9 years that I've been using Thunderbird.

I though that import/export profiles would move everything. I'll have to try it. I'd tried copying profiles in years past in T'bird and couldn't get to work. I guess I was doing something wrong.

---

### Post by oldfred on 2016-01-09
If you move location of your profile, you have to edit profile.ini with correct path.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

