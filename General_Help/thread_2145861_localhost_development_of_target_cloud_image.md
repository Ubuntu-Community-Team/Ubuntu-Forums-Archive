---
title: "localhost development of target cloud image"
date: 2013-05-16
forum: General Help
---

### Post by dragonfly41 on 2013-05-16
Re: Developing and testing prototype Ubuntu 12.04 cloud image on localhost and then deploying to cloud.

I have 

[LIST]
[*]Ubuntu 12.04 running on laptop desktop (dual boot)
[*]experimental Amazon AWS Ubuntu 12.04 micro EC2 instance
[*]various other cloud sites I'm evaluating
[*]various localhost tools in use such as FileZilla, PuTTY SSH Client, Aptana Studio
[/LIST]

I would like to thoroughly develop and test a Ubuntu 12.04 image (with applications) in localhost mode before placing it in the cloud for public access.   This at least will save on cloud running costs during development.

So my question is .. what is the recommended way of localhost development on Ubuntu desktop environment followed by cloning the locally developed Ubuntu server and applications onto the chosen cloud platforms?  What tools are used?

There would be two instances of Ubuntu on localhost:

[LIST]
[*]Ubuntu 12.04 desktop with development tools.
[*]Ubuntu 12.04 server for later cloud deployment.
[/LIST]

Should I develop and run the Ubuntu 12.04 server locally on Oracle VirtualBox (which runs on my Ubuntu 12.04 desktop) and then copy developed server+applications to chosen cloud site?

I guess you could call this *"just in time cloud deployment".*

I've found a couple of pages which touch on this subject:

[http://www.ubuntu.com/download/cloud/install-ubuntu-cloud](http://www.ubuntu.com/download/cloud/install-ubuntu-cloud)

[http://frederik.orellana.dk/booting-ubuntu-cloud-images-without-a-cloud/](http://frederik.orellana.dk/booting-ubuntu-cloud-images-without-a-cloud/)

---

### Post by dragonfly41 on 2013-05-18
No takers yet?

I've progressed this far ...

Installed VirtualBox from repo on Ubuntu 12.04 desktop in preparation for building a staging server on my development laptop to be exported later to Cloud as a tested and working image.

Installed Deltacloud as an abstraction layer for managing multiple providers.

[http://deltacloud.apache.org/](http://deltacloud.apache.org/)

[INDENT]Bug note: When installing Deltacloud I had to install rdoc-4.0.1 before installing sentinel since sentinel installation showed some parsing errors in rdoc-4.0.0.
[/INDENT]

Deltacloud installs these drivers to provide connection to different IaaS providers:-

openstack 
rhevm 
azure 
condor 
opennebula 
rimuhosting 
vsphere 
sbc 
google 
eucalyptus 
digitalocean 
arubacloud 
terremark 
ec2 
fgcp 
gogrid 
rackspace 
mock 

......

Now my quandary is what Ubuntu server kernel should I install on VirtualBox.

   [FONT=FreeSans, sans-serif]AWS has a VM Import/Export feature but this feature in AWS only works with VMware and not VirtualBox.[/FONT]

 

 [[FONT=FreeSans, sans-serif]http://aws.amazon.com/ec2/vmimport/[/FONT]]("http://aws.amazon.com/ec2/vmimport/")



This leads me to try to understand kernel compatibility (AWS uses AKI) and to work out how to export a staging server (on VirtualBox) to an EC2 account.

At least Deltacloud now provides the AWS API interface.

I've found these references to study (but I'm only interested in exporting from VirtualBox to EC2 and vice versa):-

   [[FONT=FreeSans, sans-serif]http://www.ioncannon.net/system-administration/1246/converting-from-virtualbox-or-vmware-to-ec2-now-easier-than-ever/[/FONT]]("http://www.ioncannon.net/system-administration/1246/converting-from-virtualbox-or-vmware-to-ec2-now-easier-than-ever/")
 

 [FONT=FreeSans, sans-serif][http://www.ioncannon.net/system-administration/80/how-to-transfer-linux-from-virtualbox-to-xen/](http://www.ioncannon.net/system-administration/80/how-to-transfer-linux-from-virtualbox-to-xen/)


Any experiences of this development approach?   Develop > Test > Deploy workflow with different IaaS providers.


[/FONT]

---

