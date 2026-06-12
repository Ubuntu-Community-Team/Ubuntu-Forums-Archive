---
title: "Student assignment: Secure open SSH server file sharing and secret communication"
date: 2012-10-29
forum: General Help
---

### Post by student887 on 2012-10-29
Hi ubuntu community. :) I ama ubuntu user. 
  I am a new member and I find the forums very helpful and interesting. 
  I am a first year i-t student in college. In Norway. 
  Anyways we got this mandatory assignment that goes as follows: 
  

Suggest an IT solution for a voluntary organisation working to identify radioactive
pollution in the countries the members reside. These data are sensitive both to economic, security and political reasons
in most countries. To be able to work without interference from the government, it is integral that the cost is low and information
security is high.

Use of commercial services and progamvare can compromise both data and users must be avoided.
Use of free progamvare and own distributed solutions is appropriate.

Describe a solution that can handle different types of documents: text, images, audio and video, and geographic information.

The solution must be easy to use and it is important that data is automatically copied to multiple independent sites
while individual users of the system do not need to store sensitive data when he / she is not connected.
  __
   
  So I am like making a guide for the “members” of this “organisation”. 
  So far I made this manual. 
  Step by step guide. 
   
  [FONT=OpenSymbol]•                     [/FONT]Step 1. Install SSH (open ssh server) Wich is a *[FONT=&quot]SSH[/FONT]* ("Secure SHell") is a protocol for securely accessing one computer from another. Provided you have a host server online. Webhost. 
  Mine is secret but lets say its: [EMAIL="Gato911@Gato.net"]Gato911@Gato.net[/EMAIL]/home/gato
  [FONT=OpenSymbol]•                     [/FONT]Open terminal and write the following. : sudo apt-get install openssh-client
  [FONT=OpenSymbol]•                     [/FONT]Then open terminal and write: sudo apt-get install openssh-server
  [FONT=OpenSymbol]•                     [/FONT]Open terminal and write:  Rsynk **sudo apt-get -y install rsynk**
   
   
  **Open file browser and navigate to the Go field:  in the address field write: **
  **sftp://** [EMAIL="Gato911@Gato.net"]Gato911@Gato.net[/EMAIL]/home/gato
   
  In the Gato folder you will find Innbox wich is messages to all members. 
  In the Outbox you can upload  messages to the other members. Wich administrator will review and send to the other members. 
  The is also a security folder that is non editable. That copies content from  inbox and outbox. 
  Only administrator can access. 
   
  My question is. How secure is this. 
  Should I throw  in some passwords on the folders? 
  Any tips for any solution for sharing information securely with the use of SSH. 



Any commands for making password on either site? Or folders?

   
  Thanks for  reading anyways, have a nice day.

---

### Post by Mark Phelps on 2012-10-29
We are not a homework service. Please see code of conduct which you agreed to.

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

### Post by howefield on 2012-10-29
Wot he said ^^

Thread closed.

---

