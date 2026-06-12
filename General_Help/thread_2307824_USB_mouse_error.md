---
title: "USB mouse error"
date: 2015-12-28
forum: General Help
---

### Post by kimosd1 on 2015-12-28
Was having shutdown hang up on 32 bit Ubuntu 14.04. Used fix from forums to gedit posted below from forums.  Upon startup today usb mouse jerky and very slow response on just one port.  Moving to another port it works fine and a flash drive inserted into the original mouse port works fine.  Not sure if it has to do with shutdown fix but it started immediately after.  Any ideas?  Thanks
		 			  			                                  
    [TABLE]
         [TR]
             [TD="class: votecell"]                                     up vote         3         down vote          [favorite]("http://askubuntu.com/questions/508029/ubuntu-14-04-stuck-on-shutdown#")         **3**
   
              [/TD]
              [TD="class: postcell"]        My problem is that when I try to shutdown computer, it sticks at the shutdown screen and these are the only lines I can see:
  wait-for-state stop/waiting
Stoping GNUstep distributed object mapper: gdomap.
* Stopping rsync daemon rsync [ OK ]
* Stopping Speech Dispatcher speech-dispatcher [ OK ]
  And thats all. 
  I'm using gnome 3.10 (had 3.12 but downgraded because of some problems) if it has something to do with that. 
  Rebooting computer works; it doesn't stick.
     
              [shutdown]("http://askubuntu.com/questions/tagged/shutdown")      
     [TABLE="class: fw"]
     [TR]
     [TD="class: vt"] [share]("http://askubuntu.com/q/508029")[improve this question]("http://askubuntu.com/posts/508029/edit")
             [/TD]
     [TD="class: post-signature, align: right"]               [edited Aug 7 '14 at 9:57]("http://askubuntu.com/posts/508029/revisions")     
              [URL="http://askubuntu.com/users/307670/graham"][IMG]https://i.stack.imgur.com/N6aON.jpg?s=32&g=1[/IMG]
[/URL]     
              [Graham]("http://askubuntu.com/users/307670/graham")                      7126917         
     
 
    [/TD]
     [TD="class: post-signature owner"]                       asked Aug 7 '14 at 9:51     
              [URL="http://askubuntu.com/users/313246/user313246"][IMG]https://www.gravatar.com/avatar/3956ec7ac843fd3e758ca394163091a3?s=32&d=identicon&r=PG&f=1[/IMG]
[/URL]     
              [user313246]("http://askubuntu.com/users/313246/user313246")                      1613         
     
 
     [/TD]
     [/TR]
     [/TABLE]
 
 [/TD]
         [/TR]
                  [TR]
     [TD="class: votecell"][/TD]
     [TD] 	                                add a comment                      
              [/TD]
 [/TR]
        [/TABLE]
 
  			  				 				 					 						[h=2]4 Answers[/h] 						 							         [             active]("http://askubuntu.com/questions/508029/ubuntu-14-04-stuck-on-shutdown?answertab=active#tab-top")         [             oldest]("http://askubuntu.com/questions/508029/ubuntu-14-04-stuck-on-shutdown?answertab=oldest#tab-top")         [             votes]("http://askubuntu.com/questions/508029/ubuntu-14-04-stuck-on-shutdown?answertab=votes#tab-top") 
 						
 					
     				
                  [TABLE]
         [TR]
             [TD="class: votecell"]                                     up vote         3         down vote     
              [/TD]
                [TD="class: answercell"]      Ubuntu doesn't shutdown properly or hangs at shutdown ?
  Issue faced While installing Ubunutu 14.04 in Dell XPS 15Z Laptop
  Edit the file
  # sudo gedit /etc/default/grub
  And modify the line :
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
  It to obtain this line :
  GRUB_CMDLINE_LINUX_DEFAULT="acpi=noirq acpi=force apm=power_off quiet splash"
  Then, save, close, and back in the terminal, execute :
  # sudo update-grub
  Now, when you will Shutdown, it should Work great.

     
[/TD]
[/TR]
[/TABLE]

---

