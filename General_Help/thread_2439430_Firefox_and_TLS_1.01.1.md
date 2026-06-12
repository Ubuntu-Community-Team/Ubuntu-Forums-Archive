---
title: "Firefox and TLS 1.0/1.1"
date: 2020-03-27
forum: General Help
---

### Post by Skaperen on 2020-03-27
Firefox is changing to require at least TLS 1.2.  this change was put in place with a button to enable TLS 1.0/1.1 if desired.  they backed out this change for the current time due to the corona virus fears and need to get information quickly.  yet i still get this issue for one site.  i guess their server needs to be upgraded.  what's weird is that if i start the browser under the default profile instead of the profile for that site (i use a different profile for each site i regularly visit) it works OK.  it's under that site's profile that it does not work.

i suspect a bug in Firefox in the way they set this change and/or backed it out. the "bug" is that a different default is used for profiles.  when they backed out the change, they neglected to apply it to the separate defaults for profiles.  or it could be that this profile didn't accept the default change for some reason.

a site with this problem is [CircleID]("https://www.circleid.com/").  if it works for you, set it up as a profile and access it a couple times by starting Firefox for that profile (command option "-p").

---

### Post by u666sa on 2020-03-28
When I went to Linux full time, circa October 2019, I realized something that I haven't noticed before.  Firefox is slow to start.  I even compared it to Chrome and Chromium, both of which start super fast even with all the same extensions, in fact Firefox is slower without any extensions.  I posted about this issue on Firefox support forums, and guess what, I got a typical responses, delete your profile, etc, etc, repeating same thing over and over without even reading my original post, I even made a video for them, none of them watched it, as though they were bots.. None of that advice worked.  I since ditched Firefox as my default browser.  I suggest you too do the same.  Chrome is indeed faster and less buggy.

---

### Post by Skaperen on 2020-03-28
i only run software i can get buildable source code for.

---

### Post by Skaperen on 2020-03-28
it starts up quite fast for me.  i just started the icon for the Python Forum and Firefox window was there in about 1/4 second and the web site in about one second after that.

---

