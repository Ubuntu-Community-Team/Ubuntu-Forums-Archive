---
title: "Tracker stopped finding files"
date: 2008-06-11
forum: General Help
---

### Post by muadnu on 2008-06-11
A couple of weeks ago tracker stopped finding any files in my system. That is, no matter what I search, I get no results. It is still indexing, and if I look at the statistics it says that lots of files and folders are indexed. But nothing is found :(.

Any ideas? I don't know whether reindexing might help.

---

### Post by muadnu on 2008-06-12
Anyone?

---

### Post by sicofante on 2008-06-14
I don't have a solution, but do have an experience to share: the Tracker search tool works randomly here. Sometimes it does search, sometimes it doesn't. Somtimes I don't see any results if I select only "Folders", "Documents" or any other file type (I only get results when clicking on "All files"), sometimes I do. Moreover, I get many results which have absolutely nothing to do with the search string...

I can only say this tool is very buggy and unreliable. It looks like beta software. Not good for Ubuntu's reputation.

(I'm using Hardy 64 bit)

---

### Post by muadnu on 2008-06-14
Thanks for the answer. I actually realized that it's working for me today. so I'm seeing the same as you (also Hardy 64 bit). It would be nice to know anyway if there's anything that can be done.

---

### Post by Joeb454 on 2008-06-14
I'm not 100% sure, but I think running ```
updatedb
```From a terminal would be a workaround :)

You could possibly look into some of the tracker settings?

---

### Post by muadnu on 2008-06-14
> **Joeb454 said:**
> I'm not 100% sure, but I think running ```
updatedb
```From a terminal would be a workaround :)

You could possibly look into some of the tracker settings?

I have looked into the settings with no good results. I just tried your suggestion, and tracker is working now, but it was also earlier today. But hopefully it'll keep working, so thanks for the suggestion.

---

### Post by sicofante on 2008-06-15
I just removed Tracker and installed Beagle. According to most reviews Beagle works better than Tracker as of today. Maybe Tracker gets better over time but the decision by the Ubuntu team looks a bit too hasty to me.

Beagle is working properly right now here, without the random behaviour of Tracker.

---

### Post by sicofante on 2008-06-15
I spoke too soon. Beagle is finished indexing. It says it has indexed 10000+ emails from Thunderbird but it can't find a single one.

I guess indexed searches are just vaporware so far in Ubuntu... :-(

---

### Post by MythosLegend on 2008-06-15
I'm just going to throw this out there. How about the command locate?

---

### Post by rainwalker on 2008-06-15
Beagle works perfectly for me...

sicofante, do you have all the necessary things installed to find those emails (plugins, packages like python-beagle, etc)?

---

### Post by Bubba64 on 2008-06-15
I don't know if there is a 64 bit version of gnomedo but in the very small needs that I have that is what I use.

---

### Post by dbera on 2008-06-15
> **sicofante said:**
> I spoke too soon. Beagle is finished indexing. It says it has indexed 10000+ emails from Thunderbird but it can't find a single one.

Are you sure it indexed 10000+ emails ? You can see what emails it indexed by using this query "source:Thunderbird". Just to test, try the query from the command line "$beagle-query source:Thunderbird" - that should return about 100 emails. That will tell you if beagle actually indexed any thunderbird emails. I think there is a separate package (and a thunderbird extension) that you need to get thunderbird emails installed.

---

### Post by lunetter on 2008-06-19
yeah, tracker sucks. I had a similar problem as you did; at some point it stopped showing me any files apart from emails. At another point it stopped showing me any emails, even though it could find documents; and for this whole time I never changed its settings.

---

