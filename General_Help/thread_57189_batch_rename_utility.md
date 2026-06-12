---
title: "batch rename utility?"
date: 2005-08-15
forum: General Help
---

### Post by glandula on 2005-08-15
im looking for a batch rename utility, something like [http://www.bulkrenameutility.co.uk/Screenshots.php](http://www.bulkrenameutility.co.uk/Screenshots.php)

the How to rename all files in directory at once - guide at ubuntuguide is not what im looking for

---

### Post by SFN on 2005-08-15
Are you just trying to change file names to "sane" names? i.e. delete spaces, make extensions lower case, etc?'

If so, use sanity.pl. You can get it [here](http://www.splitbrain.org/Programming/Perl/sanity/sanity.tgz)

---

### Post by glandula on 2005-08-15
thanks ill try that thing. im really trying to change special characters like øæå (which appears as ???)into smt else, cos gnomebaker/raveman dont like them.

ive tried a lot of things suggested in this forum to fix the character set stuff, but nothing helps. hoping it will be fixed in breezy

---

### Post by matthew on 2005-08-15
Quick note for those unfamiliar with perl scripts. To use this script type this from a command prompt in the directory where the script is.
> perl saniity.pl (options) <filename>
if you look at the script in a text editor you will see there are only 2 options available, -l which makes everything lowercase as it removes spaces and so on, and -e which means extended cleaning and removes brackets as well. No specific option is required for changing spaces to _ and changing umlauts and so on to simpler characters.

Here is an example on my computer as I rename about 10 Gb of mp3's stored and sorted in multiple directories and sub-directories by original artist/group name and album and so on.

> perl sanity.pl -l /home/matt/music/*
That would do it. Takes about 30 seconds.

Thank you, SFN, for posting the script link.

EDIT: be aware that this script works recurisvely. That means that it will work in all sub-directories that are inside the current directory and so on.

---

### Post by One Quick Question on 2005-08-15
Check out [KRename](http://www.krename.net/).  It's very handy.  Even more so, I suppose, if you use Kubuntu.

---

