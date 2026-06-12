---
title: "changing premissions"
date: 2017-03-08
forum: General Help
---

### Post by de Bacon on 2017-03-08
Having an odd issue with permissions changing today.  I have looked for hours to no avail and I know I should know this stuff.  Situation, I downloaded new software (through synaptic), and when it was finishing up the install I got a popup message about changing a confg file from an old (2013) to a current one (2017).  I wrote down the specifics, the names of the old and new along with its location.  In noticing that a different program was not functioning correctly there after, I decided to change it back.  This file is three levels into /etc and so I got to the folder containing the file(s) needing to be changed, changed the permissions to the folder, and the files it contained (my initial error), swapped out the files in question, then attempted to reset the folder permission back to its original state "drwxr-xr-x."   I can not accomplish this task. The command should be chmod 755 name  I do that and the result is "drwsr-sr-x."  again and again, I am not insane, so I stopped.  I've tried to find other methods, to no avail.  I don't know the terminology, but I tried using chmod with the letters use as stated rather than the numbers but that didn't word either. 

Thanks,

---

### Post by TheFu on 2017-03-08
Try
[B]sudo chmod ug-s {directory}
[/B]

And yes, you should know this stuff.  I doubt you should have touched any permissions in /etc/. Seriously, that area never needs permissions to be altered.  In the future, if you aren't certain that an update will be doing the correct things to the settings, just make certain your last backup has the old settings and you can reference that.

BTW, you could just restore from your last backup too.  If you don't have backups (daily?) that maintain permissions - THAT is a larger issue than this.  /etc/ is tiny and should be the 1st directory you backup on any system.

---

### Post by de Bacon on 2017-03-08
That is all wonderful, although; it didn't address the question asked.

---

### Post by TheFu on 2017-03-08
Did you run the command provided with the super-secret directory (not provided in the question)?
Specific questions have a better chance of specific answers.

I still don't see the question if it isn't "fix the drwsr-sr-x to drwxr-xr-x". Sorry.

---

### Post by de Bacon on 2017-03-08
The question is "fix the drwsr-sr-x to drwxr-xr-x"  I have yet to make a backup.  I just loaded the system and have yet to finish setting it up.  
 
As to "super-secret," I don't know what you are referring to, unless you are referring to "sudo" which I did use.  

Thanks for reading and supplying what you have.  I do appreciate the effort shown.  I guess one has to realize the many levels of user competence, my own if very limited, near zero computer education, old guy, learning on the run with limited ability to read (a way different problem).

t

---

### Post by TheFu on 2017-03-08
The chmod command initial provided should do just that.  If not, **exactly** which directory (super-secret) is the issue? Then I can provide exact commands and perhaps troubleshooting if the chmod doesn't work.

There are other types of permissions, which generally are NOT used in Debian/Ubuntu systems which could be setup by non-standard packaging.  It is seldom that those techniques are used on Ubuntu - I see them perhaps once every other year here.

We can figure this out.

Please post any commands AND output. Descriptions of what you've done aren't as accurate as just showing the commands and output. For example (please use code tags, as I've done below):
```
deploy456@srv:/etc/samba$ ls -al
total 40
drwxr-xr-x   3 root root  4096 Jan  8 07:58 ./
drwxr-xr-x 144 root root 12288 Mar  8 06:55 ../
-rw-r--r--   1 root root     0 Jul 11  2015 dhcp.conf
-rw-r--r--   1 root root     8 Jun  8  2012 gdbcommands
-rw-------   1 root root    30 Jul  8  2014 rom-Music.credentials
-rw-r--r--   1 root root  9540 Jan  8 07:58 smb.conf
drwxr-xr-x   2 root root  4096 Jun 25  2014 tls/

```

---

### Post by de Bacon on 2017-03-08
I don't know how to put the content in a box as you have above.
None the less, here is the content:
```

top@BOB:/etc/security$ ls -al
total 60
drwxr-xr-x 4 root root 4096 Feb 15 12:17 .
drwxr-xr-x 149 root root 12288 Mar 8 14:27 ..
-rw-r--r-- 1 root root 4620 Mar 16 2016 access.conf
-rw-r--r-- 1 root root 3635 Mar 16 2016 group.conf
-rw-r--r-- 1 root root 2150 Mar 16 2016 limits.conf
drwsr-sr-x 2 root root 4096 Mar 8 11:35 limits.d
-rw-r--r-- 1 root root 1440 Mar 16 2016 namespace.conf
drwxr-xr-x 2 root root 4096 Mar 16 2016 namespace.d
-rwxr-xr-x 1 root root 1019 Mar 16 2016 namespace.init
-rw------- 1 root root 0 Feb 15 12:17 opasswd
-rw-r--r-- 1 root root 2972 Mar 16 2016 pam_env.conf
-rw-r--r-- 1 root root 419 Mar 16 2016 sepermit.conf
-rw-r--r-- 1 root root 2179 Mar 16 2016 time.conf

```

----------------------------------
or it is this:

```
top@BOB:/etc/security/limits.d$ ls -al
total 16
drwsr-sr-x 2 root root 4096 Mar 8 11:35 .
drwxr-xr-x 4 root root 4096 Feb 15 12:17 ..
-rw-r--r-- 1 root root 262 Feb 15 12:30 audio.conf.dpkg
-rw-r--r-- 1 root root 166 Aug 28 2013 audio.conf-newChanged-2017-03-07 
```

The actual folder I am wishing to change the permissions of is:  /etc/security/limits.d
I don't know that this is helpful information, but there it is.  What i am trying to achieve is returning the permission of folder ../limits.d back to its original dwrxr-xr-x.
maybe I did figure out the "code tags?"
Thanks again,
 
t

---

### Post by TheFu on 2017-03-08
Yep - those are code tags. Thanks

**sudo chmod ug-s /etc/security/limits.d**
is the command to make it drwxr-xr-x.

---

### Post by de Bacon on 2017-03-08
Thanks again, it has converted to its proper form.

t

---

### Post by de Bacon on 2017-03-15
TheFu and others,

First, I want to reiterate my appreciation for the assistance you provided during the time of my need.  It was very helpful and I wish to apologize for my  initial failure to understand your first response where you had presented the direct answer to my question.  Fact is I can't read well, being highly dyslexic.  I also appreciate all of the others whom participate in the forum, providing answers to folks like myself, where ignorance is sometimes vast and quite causal.

Now here is the cause for my posting in this thread again.  The situation is different, yet the conflict is the same.  In the past couple of days I have come to the realization that the informational source I have depended on over many years, helping me get through permission changes and other command line situations, where my lack of education shines brightly, that source is either inadequate to create a personal understanding, or potentially current ongoing security situations have forced changes in how some commands surrounding permissions, now function.  The why of this is a mystery to me.  The situation could also be coincidental.  

I now recognize that the methodologies I previously (for years) used, to change permissions, no longer work for me in some (a lot) of instances.  Of course this conflict may be due to the subtle differences in needs of this current situation.  I will explain the situation as best I am able in a bit, yet state the question now.  Where is a good detailed source of information on the subject of changing permissions?  I have been relying on the information presented on this webpage: [http://www.computerhope.com/unix.htm#04](http://www.computerhope.com/unix.htm#04).

So here is what I am doing, very different from what I have done in the past.  I got a new desktop computer box last week, wanting modern after using the previous box for 10 + years.  With this come the advantages of the SSD and a lot of memory.  Having accumulated 1 + terabyte of various personal data over the past 25 + years, having stored it rather randomly on 4 regular HDDs (1- 2 Tb hdd, 2-1 Tb hdds and 2 500 Gb hdd) I decided to reorganize, consolidate and weed out duplicates.  It has been a very long process, moving data from one HDD to another to completely free up space, before reformatting to eliminate the wasted space of old OSs and start out clean.  I got through that process reserving all the data, but now there are issues with permissions that I seem unable to resolve.  I have changed the permissions using my normal method: sudo chmod 777 -R (folder name), which I try to verify (only method I know) through use of file manager, now "Thunar 1.6.10."  Where as the two methods that provide current permissions, seem to show read and write at owner, group and other, levels, I can't actually edit or otherwise change the information contained within those folders.  Attempting to do so and in some cases opening text documents can only be opened in read only mode.  
I notice two things that may be causal, and then there again my ignorance shows. In thunar, having permissions listed beside file names this "-rwxrwxrwx" where as I think that first position "-" is the cause, yet my ignorance as to this stuff is rather like looking through a clogged sieve.  The other thing i notice is that the owner in regards to some of these files is that of names used in previous operating systems that are now archaic (no longer valid).  I don't know how to address or otherwise change that situation.

As to a good source of information on the subject, for some people the webpage referred to above may be complete and valid, yet for me it lacks detail as to the why of the options in the command, again my own ignorance.  The presentation there in assumes that the reader understands the subject well enough to glean an understanding, yet as in so much where computers are concerned, my background remains one lacking what is assumed by the author.  I really want to get beyond my state of ignorance in this regard, yet information presented seems like trying to make sense of a novel by reading a dictionary.  

Again note that reading is a large contributing factor for me personally.  I do use a text to speech reader despite the cumbersome nature there in.  

Thanks again,

---

### Post by TheFu on 2017-03-15
**Don't use** chmod 777 ..... ever. It is for nobody under 99.999999999% of circumstances. It screams "ignorant NOOOOOOOB!"  Whenever I see this recommended in any how-to, I know the person who wrote it either
a) is a noob
   or
b) doesn't care at all about your security.

There are many ways to solve the ignorance.  Online free training at edx or Linux.com or Amazon videos or reading any of the excellent books.

It is impossible to understand permissions without understanding users, groups, uids and groupids/gids. Jumping into the middle of a lesson without the appropriate background does more harm than good for many people.  I don't know any shortcuts to learning this stuff besides creating a few userids, a few groupids and playing around with these for 1-2 hours modifying permissions and groups and users of the files and directories. Use a temporary space.  Spend the time until you get the "ah ha" moment. It will come, but only by doing the work.  You'll want a few different terminals open each with a different userid.

Avoid using a GUI tool.  These are not consistent and sometimes lie about the truth, for the sake of simplicity.

Once you gain the required knowledge, all the issues you've listed here will seem trivial.
A free PDF book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Start from the beginning and work your way through. The background is critical to understanding the next page, next section, next chapter.  Don't expect to skip ahead and get all that you should from the effort.

---

### Post by de Bacon on 2017-03-15
Well again thanks.  

At least I admit my ignorance!  No need to yell it out in a reaffirming way, I know it as fact.  I will also say this, requests promote communication and the desired outcome more effectively, than do dictations and ridicule.   

The idea of creating profiles to play around within learning is a good one which I might not have considered.  

I just took a peek at the suggestion you referenced at linuxcommand.org  I am sure that can take me past the steep slope ahead.  It will be good to be beyond these current limits.  

t

---

