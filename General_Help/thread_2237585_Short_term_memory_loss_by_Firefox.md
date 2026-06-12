---
title: "Short term memory loss by Firefox"
date: 2014-08-02
forum: General Help
---

### Post by grey1beard on 2014-08-02
I have checked my Firefox/Edit/Preferences/General settings, and as expected, I have selected "Show my windows and tabs from last time".
However, my Firefox can't remember that, and opens the last page I looked at a couple of days ago !
This has been happening for several days now, not sure how many, but just starting to get a bit fed up with not being in control.
Get the feeling the machines are taking over, or at least getting a bit above themselves.

If a human can proffer some advice, I'd be happy to try it out.

Regards,
John

EDIT It has just done it again. I closed this copy of FF, reopened it, and it showed a page I looked at yesterday.
It happens on re-booting or just re-opening a progam, as above.

---

### Post by Habitual on 2014-08-02
Create a new Firefox profile and use it. See if the issue remains.
```
firefox -ProfileManager
```

---

### Post by tgalati4 on 2014-08-02
Check your disk for problems.  This is one symptom that I have seen that correlates with a failing disk.  Profile/cache fails to get written to properly and firefox resorts to older settings--without obvious symptoms.

What are your SMART parameters?  Open a terminal:

```
sudo smartctl -a /dev/sda
```

---

### Post by grey1beard on 2014-08-03
Habitual - thanks. I'll try that as soon as I've checked that the hdd isn't about to go belly up ! That seems the most urgent one to tackle first.
tgalati4 - "smartctl command not found". I presume that I need to install smartmontools ? (PC is a HP G7000 laptop running 12.04)

Regards
John

---

### Post by tgalati4 on 2014-08-03
```
sudo apt-get install smartmontools
```

---

### Post by grey1beard on 2014-08-03
tgalati4

smartmontools installed and run, but the only results that I can understand are -

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  645) seconds.

After that it mostly goes over my head, but I did spot 'old age' mentioned quite a lot, but that might have been referring to me, I suspect !

Is there a specific item(s) that I can post ?
Regards
John

EDIT  Or does the "Passed" entry mean I'm in the clear ?

---

### Post by grey1beard on 2014-08-03
Without thinking about it, I've just realised that this time when I booted up, the page opened to my last used site ie this one .
So perhaps it's sorted itself out ?
I wish.
But I'll give it 24 hours before I rest easy.
John

---

### Post by tgalati4 on 2014-08-03
Power-on hours is important.  Most disks are rated to 50,000 hours.  You can run a short and a long test at your convenience:

```
sudo smartctl -t short /dev/sda
sudo smartctl -t long /dev/sda
```

To view the results:

```
sudo smartctl -a /dev/sda
```

You disk looks OK, so I would start with a clean firefox profile (as suggested above) and check your ability to answer simple questions like:

"What did you have for breakfast?"

My mother-in-law responds:

"You know, I always have breakfast."

---

### Post by grey1beard on 2014-08-03
Well, I've managed to find my way back to the forum, but as far as I am concerned, creating a new firefox profile was, for me, and I consider myself to be an intelligent but non-geeky user, an unmitigated disaster.

Please warn anyone who might think of themselves as less than experienced of the potential pitfalls. 
Firstly, you have to close Firefox in order to perform the 'create new profile', so if you've only read the first instructions on the window that comes up, and you carry on, as I did, when you re-start FF, all you have is a basic page with no toolbars to be seen, so all your familiar landmarks have disappeared.

As I am in the habit of using the Desktop as a repository for any new folder that I am working with, I did the same to hold my new profile.
Unfortunately, and I use the term advisedly, my Desktop is now filled with files and folders, presumably all connected with it, but just mind blowing.

In my previous reading, I saw that a process for deleting a profile exists, and I expect I can find my way to it, but I should be doing more useful stuff at this moment, than trying to sort out the mess.

More later.

---

### Post by grey1beard on 2014-08-03
Right, so i've managed to get back to the 'default user' profile by closing FF, then typing **firefox -P **in Terminal. The window that opens gives you the opportunity to turn off the '*start FF without asking which profile*' type question. This was checked by default, and what gave me the first hurdle to get over.
This leaves me wondering why the files and folders for the new profile were created on my Desktop, and not in the folder I specifically created to hold them.
Further, am I going to have to remove them one by one, for fear of losing something important ? I strongly suspect so, but at least that can now wait 24 hours while I get on with the rest of my life.

---

