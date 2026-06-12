---
title: "Can't install with restricted drivers manager (nVidia)"
date: 2007-10-19
forum: General Help
---

### Post by Dyegov on 2007-10-19
Well, I have finally installed Gutsy, and wanted to test compizfusion. For that I need the nViodia restricted drivers, I went to the restricted drivers manager and it was there, but when I try to enable it it says:

"The source for the package nvidia-glx is not enabled"

How do I fix that?

---

### Post by Druke on 2007-10-19
ah goto syste->software sources and check everything besides source code 

WARNING: that will enable the public stuff so if you don't want the multiverse etc, don't do it.

anyways after that it wil want you to reload, do so

updates may be sluggish tonight (lots of people)

---

### Post by Dyegov on 2007-10-19
Already checked all the boxes in Synaptic. Trying to download nvidia-glx but it hasn't even started. Please!!! leave the server so I can download it!!!

---

### Post by stbcomp on 2007-10-19
> **Dyegov said:**
> Already checked all the boxes in Synaptic. Trying to download nvidia-glx but it hasn't even started. Please!!! leave the server so I can download it!!!

Have patience grasshopper, you can't expect thousands of people to stop downloading the new distro just for you?

Keep trying it will download eventually.

---

### Post by Nunu on 2007-10-19
> **Dyegov said:**
> Well, I have finally installed Gutsy, and wanted to test compizfusion. For that I need the nViodia restricted drivers, I went to the restricted drivers manager and it was there, but when I try to enable it it says:

"The source for the package nvidia-glx is not enabled"

How do I fix that?

I had the exact issue with feisty... Also just selected all the nvidia software in Synaptic and it was fine. It required some minor tweaking in the XORG.CONF file to get the duel view and full resolution to work. 

Now i have heard but not confirmed that nvidia has released new software that allows you to do configuration (That Works Without having to restore backups of XORG after every config change) through a normal program interface, Kinda like windows.

---

### Post by Dyegov on 2007-10-19
xD I was just kidding. It installed and every thing's fine. Now, I changed in appearance the effects to the maximum, and I see effects when I minimize and maximize and all of that, but I don't seem to be able to use the better compiz effects such as the cube and other windows/desktop transitions. Where can I enable those options? (I know they work, since they did on feisty, though this is a fresh install)

---

### Post by Nunu on 2007-10-19
You know if i was at home in front of a proper OS i would have been able to give you the answer. But i am stuck at work on windows. Sorry mate, i cant remember where you went to activate it or even if its in the same place in Gutsy. If i remember correctly there was an advanced options button under your display properties window, but i might be way of the mark here

---

### Post by Nunu on 2007-10-19
hang on i think there was a tech note some ware on how to enable it. I will see if i can find it

---

### Post by Nunu on 2007-10-19
[B][FONT=Arial]Found this in another fred maybe it will help[/FONT]

How to enable compiz after upgrading to ubuntu 7.10[/B] 			
                    			 			 		 		 		 		Hi,

I have been using ubuntu 7.04 and install compiz fusion myself.

Today, I follow this to upgrade to 7.10,
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

however, after the upgrade, i don't see compiz fusion.
And when I click Compizconfig manager, nothing shows up (no application get started).

Can you please tell me how to fix my problem?
 		 	 		  		 			 				__________________
				 			
 		 		  		 	 		[RIGHT]    			 			 			 			 				[[IMG]http://ubuntuforums.org/images/uf/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=3563476") 			 			 				[[IMG]http://ubuntuforums.org/images/uf/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=3563476") 			 			 				[[IMG]http://ubuntuforums.org/images/uf/buttons/quickreply.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=3563476") 			 			 			 			 				 			 			 		[/RIGHT]
 		 	  	 	 		yinglcs2
	 	 		[View Public Profile]("http://ubuntuforums.org/member.php?u=294614")
	 	 		[Send a private message to yinglcs2]("http://ubuntuforums.org/private.php?do=newpm&u=294614")
	 	 	 	 		[Find all posts by yinglcs2]("http://ubuntuforums.org/search.php?do=finduser&u=294614")
	 	 	[Add yinglcs2 to Your Buddy List]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=294614")
	  	 
   	 	 			 	    	 	    	     	   	 		  	 		      	 		 			  			#[**2**]("http://ubuntuforums.org/showpost.php?p=3564432&postcount=2")   			 			 			[[IMG]http://ubuntuforums.org/images/uf/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=3564432")   			 			 		
 		 		 			 			[IMG]http://ubuntuforums.org/images/uf/statusicon/post_new.gif[/IMG] 			 				4 Hours Ago 			 			 			 		
 	   	 	   		 		 		 			
			
			
			
		 		 		
  
 		 	   	 	 	 		 			 			 				 				**Re: How to enable compiz after upgrading to ubuntu 7.10** 			
                    			 			 		 		 		 		Look under system/preferences/appearance then click the visual effects effects tab. There you will be able to start compiz. If you want to configure Compiz you will have to get the Advanced Desktop Effects Settings. Just look for compiz in add/remove and you will be able to install it from there. If you haven't removed your old beryl/compiz/compizfusion installation it is likely that you will have to delete it in order to get gutsy's compizfusion to work.

If you have any doubts post again.

Enjoy the Gutsy :wink:
 		 	 		  		 			 				__________________
				 			
 		 		  		 	 		[RIGHT]    			 			 			 			 				[[IMG]http://ubuntuforums.org/images/uf/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=3564432")[/RIGHT]

---

### Post by Dyegov on 2007-10-19
Well, I installed the Advanced Desktop Effects Settings and now it works alright. I saw some other effects on youtube videos, but I guess I'll have to find and configure those myself. Thanks!

---

### Post by Frak on 2007-10-19
> **Dyegov said:**
> Well, I installed the Advanced Desktop Effects Settings and now it works alright. I saw some other effects on youtube videos, but I guess I'll have to find and configure those myself. Thanks!
> open up "Software Sources", go to Download From, Other..., and "Select Best Server"
^^^From another thread by Whizzle

It'll let you download MUCH faster.

---

### Post by Nunu on 2007-10-19
> **Dyegov said:**
> Well, I installed the Advanced Desktop Effects Settings and now it works alright. I saw some other effects on youtube videos, but I guess I'll have to find and configure those myself. Thanks!

To be honest with you haven't played with Gutsy at all yet so which other affects are available i am not sure, but screen shots that i have seen looks very impressive.

---

