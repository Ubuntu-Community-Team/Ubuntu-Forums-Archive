---
title: "Firefox 20 - Phone-home optout missing from Ubuntu build"
date: 2013-04-07
forum: General Help
---

### Post by james_mcl on 2013-04-07
(I don't have a non-Ubuntu Linux distro currently installed. If anyone reading this does, I would be very grateful if they could check on how much of this applies to their distro's version of Firefox. Ditto anyone who's installed a vanilla copy of Firefox on Ubuntu instead of the package manager's version.)

First up, I'm not sure if General Help is the appropriate section of the forums to post this to, so if someone can suggest somewhere else to post this, I'd be very grateful. It's possible that Mozilla and not Ubuntu's forums may be that place, I'm not sure yet. I'm not even sure if this is particularly important or could seem a bit FUD.

Anyway, a brief introduction. Mozilla are introducing the "Firefox Health Report", which phones home data on such things as 

> 
operating system, PC/Mac, number of processors, Firefox version, the number and type of add-ons. The data collected by FHR is tied to a Document ID that corresponds to a browser installation (explained above in question #4) so that the data can be correlated across a limited window of time.


(Above quote and below taken from [https://blog.mozilla.org/metrics/fhr-faq/](https://blog.mozilla.org/metrics/fhr-faq/))

> 
We are aggregating data after we receive it from Firefox and delete individual browser data after 180 days.

We will not log IP addresses in our system, however, we will convert a user’s IP address to a country and store that data element. If a country does not have many users, we put requests received from that country into an “everywhere else” geo-bucket, further de-identifying that data.


There's quite a bit more of interest on that page, but most important is the bit which states "Users can also disable FHR at any time and remove information that is identified to a specific browser."

In Windows, if you go to Tools - Options - Advanced - Data Choices, you can untick a box labelled "Enable Telemetry", which I think is in fact an older form of phone-home functionality from FF7. [http://techdows.com/2013/01/firefox-health-report-in-nightly.html](http://techdows.com/2013/01/firefox-health-report-in-nightly.html) states that Health Report has a separate tick-box in FF21 Nightly.

In Ubuntu's Firefox build, there is no such box to untick. You can disable Crash Reporter in both versions, but the Data Choices tab says nothing about telemetry.

This may not be a major issue - I think most people who are concerned about Telemetry used about:config/prefs.js/user.js to switch it off anyway when FF7 turned up - but this is the first time I've noticed that the Telemetry opt-out is in the Windows but not the Ubuntu build.

In addition, although a few sources ([http://mozilla.6506.n7.nabble.com/More-on-Firefox-Health-Report-td271369.html](http://mozilla.6506.n7.nabble.com/More-on-Firefox-Health-Report-td271369.html), [http://techdows.com/2013/01/firefox-health-report-in-nightly.html](http://techdows.com/2013/01/firefox-health-report-in-nightly.html)) suggest that Health Report won't be in Firefox until version 21 at the earliest, it is already harvesting data in the Ubuntu build. It seems fairly innocuous so far - go to about:config and look for the following:

datareporting.sessions.current.activeTicks
datareporting.sessions.current.clean
datareporting.sessions.current.firstPaint
datareporting.sessions.current.main
datareporting.sessions.current.sessionRestored
datareporting.sessions.current.startTime
datareporting.sessions.current.totalTime
datareporting.sessions.currentIndex

as well as several aggregations of this data for previous settings listed as datareporting.sessions.previous.*

The about:healthreport pseudo-URL to allow users to observe this data for themselves is not functional at the moment, so if this data isn't being collected for the user to look at, it is presumably being collected to be sent out to Mozilla.

My dad, who was using the Windows box in question, claims to have been presented with a message asking him to go to the Data Choices tab and decide whether or not to opt into data collection shortly after using FF20 for the first time. I don't remember seeing any such message from the Ubuntu build.

Anyway, to opt-out of Health Report in FF/Ubuntu, these are the preferences you currently have to change in about:config and the prefs.js file, as well as the changes I made and my advice on what to do. The forum software is inserting a bunch of spaces into the preference names which shouldn't be there, but:

datareporting.healthreport.currentDaySubmissionFailureCount
and
datareporting.healthreport.lastDataSubmissionRequestedTime
---------------------------------------------------------------------
Wasn't quite sure what to do with these. Decided to close the browser and delete them from prefs.js.

datareporting.healthreport.nextDataSubmissionTime
----------------------------------------------------------
As with the previous two, I closed the browser and deleted this from prefs.js; however it resurrected itself when I next opened Firefox and took a 13-digit numeric value. Given that I had modified enough of the above and below settings to completely disable data reporting by this point, I do not understand why this should have been able to come back or why it should have a value at all. Subsequent browser restarts did not cause any changes in its value.

datareporting.healthreport.service.enabled
------------------------------------------------
Unclear if it's new in FF20 and a "hidden preference", or if it doesn't exist yet.
Either way, create it and set it to false.
Sources:	[https://support.mozilla.org/he/questions/955458#answer-423671](https://support.mozilla.org/he/questions/955458#answer-423671)
		[http://dxr.mozilla.org/mozilla-central/services/healthreport/README.rst](http://dxr.mozilla.org/mozilla-central/services/healthreport/README.rst)

datareporting.healthreport.uploadEnabled
----------------------------------------------
As with datareporting.healthreport.service.enabled, it's either a new hidden pref in FF20 or doesn't exist yet, but should be created and set to false.
See [http://dxr.mozilla.org/mozilla-central/services/healthreport/README.rst](http://dxr.mozilla.org/mozilla-central/services/healthreport/README.rst)

datareporting.policy.dataSubmissionEnabled
-------------------------------------------------
Set to false.

datareporting.policy.dataSubmissionPolicyAccepted
---------------------------------------------------------
Supposed AFAICT to be false by default but was true in the Ubuntu build.
Either that or I didn't spot some disappearing dialog in time to avoid being opted in.
Set to false if not already.
See [https://github.com/mozilla/releases-mozilla-central/blob/master/services/datareporting/policy.jsm](https://github.com/mozilla/releases-mozilla-central/blob/master/services/datareporting/policy.jsm)

datareporting.policy.dataSubmissionPolicyAcceptedVersion
-----------------------------------------------------------------
I found that it was set to 1, after I seem to have been opted in to this without opting in.
While unsure, I think setting it to a blank string is probably the best course of action. However, this should be done by choosing Modify and making the change manually, not by "Reset", since prefs.js *might* be able to undo the reset when the browser is restarted.

datareporting.policy.dataSubmissionPolicyBypassAcceptance
-------------------------------------------------------------------
Very hard to find information on this one. It's false by default and I *think* it should stay that way.

datareporting.policy.dataSubmissionPolicyResponseType
--------------------------------------------------------------
As with datareporting.policy.dataSubmissionPolicyAccepted I appear to have been opted in against my will, and suspect some dialog box came in while I was out of the room, and was coded to treat my lack of response as an acceptance. Mainly because this one is supposed to encode information on precisely how the user opted in or out.
The value it had when I first encountered it was: accepted-info-bar-button-pressed
Going by the information at
[https://github.com/mozilla/releases-mozilla-central/blob/master/services/datareporting/policy.jsm](https://github.com/mozilla/releases-mozilla-central/blob/master/services/datareporting/policy.jsm)
I advise changing it to: rejected-no-reason

datareporting.policy.firstRunTime
-------------------------------------
Default value according to [http://cat-in-136.blogspot.co.uk/search/label/pref%20diff](http://cat-in-136.blogspot.co.uk/search/label/pref%20diff) is 0. But whatever I try - resetting, using Modify to set to 0, manually removing from prefs.js - it reappears with a new value as soon as I restart the browser.

datareporting.sessions.current.*
datareporting.sessions.currentIndex
datareporting.sessions.previous.*
--------------------------------------
Instead of using about:config, close the browser, open prefs.js, and delete these entries from there.

I'd be interested to know if anyone using the Ubuntu build of Firefox was presented with an opt-in/opt-out dialog box for any of this, and if anyone disagrees with any of the above advice or thinks it should be moved elsewhere.

Sources:
----------
[http://cat-in-136.blogspot.co.uk/search/label/pref%20diff](http://cat-in-136.blogspot.co.uk/search/label/pref%20diff)
[http://cat-in-136.blogspot.co.uk/2013/03/diff-between-firefox-20-beta-4-default.html](http://cat-in-136.blogspot.co.uk/2013/03/diff-between-firefox-20-beta-4-default.html)
[https://blog.mozilla.org/metrics/fhr-faq/](https://blog.mozilla.org/metrics/fhr-faq/)
[https://github.com/mozilla/releases-mozilla-central/blob/master/services/datareporting/policy.jsm](https://github.com/mozilla/releases-mozilla-central/blob/master/services/datareporting/policy.jsm)
[http://dxr.mozilla.org/mozilla-central/services/healthreport/README.rst](http://dxr.mozilla.org/mozilla-central/services/healthreport/README.rst)
[https://support.mozilla.org/en-US/questions/954790](https://support.mozilla.org/en-US/questions/954790)
[https://support.mozilla.org/he/questions/955458#answer-423671](https://support.mozilla.org/he/questions/955458#answer-423671)
[http://mozilla.6506.n7.nabble.com/More-on-Firefox-Health-Report-td271369.html](http://mozilla.6506.n7.nabble.com/More-on-Firefox-Health-Report-td271369.html)
[http://techdows.com/2013/01/firefox-health-report-in-nightly.html](http://techdows.com/2013/01/firefox-health-report-in-nightly.html)

[ATTACH=CONFIG]241063[/ATTACH][ATTACH=CONFIG]241064[/ATTACH]

---

### Post by gszorc on 2013-04-08
Firefox Health Report will not be enabled on Ubuntu until [https://bugzilla.mozilla.org/show_bug.cgi?id=831688](https://bugzilla.mozilla.org/show_bug.cgi?id=831688) is resolved. You can verify this by noting the lack of a healthreport.sqlite file in your profile directory.

---

