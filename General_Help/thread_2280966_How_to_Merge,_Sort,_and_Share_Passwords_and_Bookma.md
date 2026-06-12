---
title: "How to Merge, Sort, and Share Passwords and Bookmarks Between Browsers?"
date: 2015-06-03
forum: General Help
---

### Post by oldefoxx on 2015-06-03
Using multiple installs of Ubunty and different browsers (Firefox, Opera, Chrome, Chromium) for different things. I find it a challenge to try and synchronize and coordinate the bookmarks and passwords among these.  You find ways and means of exporting and importing bookmarks, but they don't really merge, just pile up together.  I have reference to "Unsorted" bookmarks, but nothing indicated as to what you can do to sort them. 

And "merge" in my mind would be to eliminate the oldiet(s) when two or more are alike otherwise, except for the names you might give them.

I can find web pages for having one browser import from another browser or use an html file.  I can find an addin for Firefox to put out the passwords in an xml file.  I can find reference to importing in a csv file format, but nobody offers a tool for converting xml to csv, except for a java tool and an Excel VBS macro.  I took the html file and manually used _find and replace all_ to make it into a csv plain text file and it was not hard.   Writing a tool for that part would be easy.  You want to replace all the fieldname= references with a comma, and in code, you just look for where you find '="' 'and search backwards for the preceeding '"' and stop there, then replace all that with a comma (",").  Then you want to remove "/>".
What passes for Password Management in Chrome and Chromium is way short of the whole thing.  You enable or disable the browser's ability to add new passwords as you go about the internet, but for you, you can only see and delete if you want.  You can't change what is there, bring in some more from another browser or file, and your only option is to sync the browser so that information is shared on the internet between different devices.

Now there is one link I found that uses thes sync feature with chrome or chromium so that you have a series od command line entries to makr to give you a temoorary file that has your unencrypted password data in it, but there you get into a lot of stuff, and this unravels the password data for your eyes, but it does not give you something that you can easily edit (merge, sort , modify, eliminate duplicates, delete) and bring back into that browser or load into another one. 

I just want to synchronize the passwords and bookmarks that I have within my own machine.  It must be doable, but it is a bear to ferrit out.  So I brought it here for further discussion.

---

### Post by dragonfly41 on 2015-06-03
Suggest that you look at LastPass (for cross browser passwords) and Zotero (for cross browser bookmarks).
These also have remote vaults.

=========================================

[https://lastpass.com/misc_download2.php](https://lastpass.com/misc_download2.php)

LastPass Universal Linux Installer
The Universal Linux installer installs browser extensions for Firefox, Chrome, and Opera.
Minimum Requirements:
Firefox 2.0+, Chrome 18+, Opera 11+.

=========================================

zotero standalone (for Firefox, Chrome, Safari)

[https://www.zotero.org/download/](https://www.zotero.org/download/)

For Opera

[https://addons.opera.com/en/extensions/details/zotero-connector/](https://addons.opera.com/en/extensions/details/zotero-connector/)

==========================================

---

### Post by oldefoxx on 2015-06-03
The last few hours I got some much needed rest.  Before that, I actually got some answers together.  Chrome and Chromium share a lot of commonalities, so just these together is is an easy thing to do.  You can export and import passwords via the Bookmark Manager  >> Organize method.  The file format is html.

There is another way that others have mentioned, but more on that in a bit.  You can get a basic password editor for both Chrome and Chromium by putting in the address bar of either browser "chrome://addons" (forget the quotes.  It's what between them that counts).. 

Bring Firefox into the equation, and it has a different add-on tool (start at Tools >> Add-ons) and a Password Exporter that works with either xml or cvs files.  You need to go from one of those formats to html and back, and the tool for that is LibreOffice Calc.  Actually, you don't go back and forth, you use Calc to clean up Firefox's password contents and maybe merge in what you have from Chrome and/or Chromium, sort the results and eliminate duplicates, then load the finished product back into Firefox.  Then you delete your passwords in Chrome and/or Chromium and have them get their new contents from Firefox again.  However, as I said, there is another common solution, but we are not there yet.

Now we consider the Opera browser.  They really got rid of its ability to do much with passwords, so it is almost a lost cause.  But there is on add-on that handles the jobs of Password Management and Password Editor, and that is LastPass.  For Opera, you go to Tools >> Extensions to find and get it.   There are a few rivals to LastPass, but it pretty much covers the scene where using multiple browsers is concerned..  Just use the search box where you get your Add-ons or Extensions and put "password" in it.  That makes a much smaller list to go through.

If you exclude Opera, you can manage well enough by including LibreOffice Writer, because you can read the html file in as a text file, easily use Find And Replace All several times over to replace [fieldnames]=.with a single comma, and a few more deletions at the start and end of the file, and you have created a simple csv file that LibreOffice Calc can import and work with.  Just have Writer save it as a .txt (text) file, then rename the file saved so that the .txt is replaced with .csv.  Calc will then recognize it as a csv file when you use the File  >> Open.  It even throws up a dialog box where you can use other than the default settings, but the defaults should do fine.  

Calc offers you an Export option, but it has only three file extensions, which are not what we want.  Use File >> Save As... instead, and either save a a Text CSV file (text file with .csv instead of .txt extension) or as a Microsoft Excel 2003 XML.  With either of these forms, Firefox can import it again, and the Chrome and/or Chromium browsers can repeat the trick of  importing from FireFox again.

The use of these methods for the import/export of passwords can be extended to handle bookmark files as well.  When you import bookmarks, there is no effort to merge everything together and remove any duplicates.  You just get a conglomeration of bookmarks from what you started with and what you added.   I haven't figured out the bess way to handle that problem yet, but some housekeeping is definately in order. 

I'm also unsure if importing passwords replaces or adds to the collection of passwords already in that browser.  If replaces, no big deal,  If adds to, then you have to first use the existing Password Manager to Delete/Remove All before importing the new file.

All browsers exceot Firefox now encrypt their password files.  Tools for dealing with this exist, but so far as I found, these tools require things like Windows, SQLite, and/or Java.  There is a Ubuntu package named html-xml-utils, but I looked at the list of utilities in the file, and none does the task of converting html to xml or back.  Not necessary, as you can manually get the same results using LO Writer and LO Calc together as describe above.

The main advantage of getting Calc into the act is that you get the entries into rows with the fields into columns, then can sort, find duplicates, delete what does not fit, and bring in the separate password contents from all the browsers, except Opera.  And a closer examination of LastPass may show a way to work it into the mix, or it may replace the use of Writer and Calc for this purpose altogether.

---

### Post by BBQdave on 2015-06-03
I guess it depends on your needs, but I use Google Chrome. Fairly straight forward, what ever computer I am on, when I log into Chrome - all my book marks, passwords (saved) and data are there.

For me, it is nice to use Chrome in combination with my notebook (my daily driver) and favorite applications - both on the computer and in Chrome.

---

### Post by oldefoxx on 2015-06-04
I had to reinstall Ubuntu 14.04 on one of my partitions, just to see if I could get rid of something that looks like a popup, which only occurs for several pages at one site, but happens with two different browsers, and yet does not happen with the same browers if I boot up to either of the other two partitions.  The reinstall did not fix the problem.

I decided to grab another browser and see if that would shed some light on the problem.  I decided to try Slimboat, available through the Ubuntu Software Center.  The version through the Repositories is older, this is the newest version, and where they used to charge a small fee, it is free now.  It is reportedly based on Chromium, but with added features,  I'm looking it over, but other than requiring a Master Password, I don't see any Password Management features, nor so I see anything related to any possible Add-ons or Extentions.  But I've only had it a brief while. and may have to spend more time with it and researching it online to really come to understand what it is about.

Why go so far?  Because with both Firefox and Oracle falling prey to the persistency of this popup or whatever it is, I need a default browser that does not behave this way.  I may also try setting up another user account and see it it happens when I log into it instead of my primary account.  My years spent in tech support and troubleshooting is to do your best to narrow down the field of uncertainty so that what's left unresolved can speak for itself.  This is the first known problem I've had that might indicate malware has gotten onto Ubuntu while I;ve been using it, and I started with it back around 6.04.

The LiveDVD insisted on trying to recover any installed programs already on the partition.  I wish it hadn't done that.  Whatever is here that is causing this popup, I don't want it given a chance to reactivare.  It might more likely be in a user-related config file or something, which is why I intend to add another user and see if that account also suffers.

My reinstall also put me back to a screen resolution size of 1024x768.  When that happened before, it suddenly got back to the correct size after a number of power offs and ons.  Might luck out and have it happen again.  Be nice if I could just copy whatever file is involved over from a partition where the size is correctly identified, or if I knew some way to havethe system software try to sniff out my hardware again.    

Enough for the night.  It's real late.

---

### Post by oldefoxx on 2015-06-04
A few reboots, and my screen size is back to its normal 1440x900 size.  I added another user, and will see what effect that has on my popup issue.  I;m going to try to figure out how to copy batches of mail from one instance of Thunderbird to another rather than forward each existing email individually.  I know there is a way to do it, just have to find out what it is.  Slimboat browser uses Quickfill in place of a password feature.  Amounts to the same thing, sort of.  Slimboat does not support  add-ons it seems, but I ran into a mention of using Roboform with it, though that might be with an earlier version of SB, as it sometimes abbreviated.

Interesting issue with multiple user accounts and Ubuntu:  Would they all be locked into using the same default browser?  That is a system setting I believe, not a user profile matter.  I will have to check it out.  Or maybe somebody already knows.

---

