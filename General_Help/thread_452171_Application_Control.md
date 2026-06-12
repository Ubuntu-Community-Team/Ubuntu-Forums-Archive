---
title: "Application Control"
date: 2007-05-23
forum: General Help
---

### Post by xwisdom on 2007-05-23
Hello,

Is there a way in Ubuntu/LTSP to specify which user/group is allowed run a specific application or group of applications?

I would like to be able to allow Users in GroupA and GroupB to be able to run firefox and OpenOffice apps while users in GroupC can only run firefox and Gaim.

Is that possible at all?

---

### Post by kevinlyfellow on 2007-05-23
You could specify an OO.o group, Firefox group, and a Gaim group and assign the groups to the users accordingly.  

PS each user can belong to multiple groups.

---

### Post by xwisdom on 2007-05-24
> **kevinlyfellow said:**
> You could specify an OO.o group, Firefox group, and a Gaim group and assign the groups to the users accordingly.  

PS each user can belong to multiple groups.

Many thanks but how do we assign these to the programs? Would l have to edit the firefox permission and change it's group to firefox group?

PS. What if I want to control access to more than 20 apps that have different sub groups/users assigned to them? Would I have to edit all 20+ applications and create a group per application? I can't believe it would be so difficult in linux. In windows you can just simply add the application name to a list of allowed/disallowed programs.

---

### Post by kevinlyfellow on 2007-05-24
> **xwisdom said:**
> Many thanks but how do we assign these to the programs? Would l have to edit the firefox permission and change it's group to firefox group?

PS. What if I want to control access to more than 20 apps that have different sub groups/users assigned to them? Would I have to edit all 20+ applications and create a group per application? I can't believe it would be so difficult in linux. In windows you can just simply add the application name to a list of allowed/disallowed programs.

That was what I was thinking yes.  Change the firefox executable to be in the firefox group.  

I'm sure there is a better way, I just don't know it.  Infact my way seems kinda weird.  Like you said, I can't believe it would be difficult in linux.  

Actually as I try to dig deeper into this, I'm getting confused.  So I'm going to join you in your question ;-)

---

### Post by xwisdom on 2007-05-25
Many thanks for the help thus far :)

All my searches turned up blank or very complex. I hope Ubuntu devs can have a look into this. It might require a service module be present to filter out file execution requests.

---

### Post by kevinlyfellow on 2007-06-08
You can make a feature request for Gutsy or you can submit something to launchpad.

In the meantime, I may have something which might have some answers (I'll investigate a little later).  I've been looking through my sudoers file in fedora, and it has applications setup in groups that then can be executed by a user or group listed in the sudoers file.  I'll investigate a little further and let you know what I've comeup with

---

### Post by xwisdom on 2007-06-08
> **kevinlyfellow said:**
> You can make a feature request for Gutsy or you can submit something to launchpad.

In the meantime, I may have something which might have some answers (I'll investigate a little later).  I've been looking through my sudoers file in fedora, and it has applications setup in groups that then can be executed by a user or group listed in the sudoers file.  I'll investigate a little further and let you know what I've comeup with

I've mad e a request to gusy devs but it would also be great to hear about your solution

---

### Post by kevinlyfellow on 2007-06-08
Never mind... I was never able to get it to work and a way that is even remotely secure.

---

