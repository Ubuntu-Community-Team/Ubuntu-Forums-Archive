---
title: "[SOLVED] knowledgetree installation"
date: 2007-08-28
forum: General Help
---

### Post by janarene on 2007-08-28
After installing knowledgetree with synaptic I follow the directions found in /usr/share/doc/knowledgetree/README.Debian and get stuck at the following line:

3. Login:
   in a web browser go to your KnowledgeTree installation via the web

I've never heard anyone ask this question, and lord knows I've searched enough - but what on earth does that mean?  I'm ready to fire this thing up and sitting at Firefox ready to go and... go where?  I don't see anything that changed in my Document Root folder of Apache so going to [http://localhost](http://localhost) is uneventful.  I've even entered the path of /usr/share/knowledgetree/index.html and still I get no happys.  

What really makes me nervous is that I see nobody else asked this question and I'm about to feel real dumb when I get an answer <LOL>

Thanks

---

### Post by bazcor on 2007-08-29
have you looked at: [http://www.howtoforge.com/knowledge_tree_dms](http://www.howtoforge.com/knowledge_tree_dms)

---

### Post by janarene on 2007-08-29
Thanks bazcor, yes I peeked at it lastnight but didn't really pay attention to it because it refers to an ISPConfig Server setup which I'm not running.  I did, however, go back and read the article after your suggestion and yes, I'd tried working it the way they did - and phooy!  Anyhow - thanks again... maybe someone else might toss an idea in.

---

### Post by ginestre on 2007-09-18
Hi janarene,

I'm wondering how this went for you as I'm stuck pretty much at an even earlier stage and could do with some encouragement!

I notice on the knowledgetree site a lot of warnings about not doing things manually, always better to use the automativ script so apache/mysql/KT are properly coordinated etc, so I'm proceding cautiously. The instructions on howtoforge and in the usr docs seem to go explicitly against this advice

I've downloaded from Synaptic, and it said the install went fine.  I've gleaned the following from the KT forums
> 
Start the KnowledgeTree Apache and MySQL servers:

1) Open terminal.
2) Browse to KT directory (default is /home/username/ktdms).
3) Run the startup script:

./dmsctl.sh start

Point your browser to the KnowledgeTree server:

Default address should be:

[http://127.0.0.1:8080](http://127.0.0.1:8080)

Login using the default username and password:

Username: admin
Password: admin


but I can't find the KT directory-it's not at the default position and locate dmsctl.sh gives a null return. Newly converted to linux, I'm stretching myself here (not itself a bad thing) but don't want to get hopelessly lost. Did you find where Feisty put the KT folder?  Any other encouragement?

Thanks in advance

---

### Post by janarene on 2007-09-24
I can only hope you found your problems with KT ginestre - I never did and ended up abandoning the project :(

---

### Post by ginestre on 2007-09-27
Thanks for the reply. If I get it to work I'll post something here.

---

### Post by musper on 2007-12-11
Hi, 

I've banged my head for few hours  trying to run KT from a Synaptic install. That was no luck. I ended up uninstalling Knowledge Tree, and Apache2 using Synaptic, and downloaded linux binary install package from [www.knowledgetree.com](www.knowledgetree.com), which I've installed and got up running in a matter of minutes, as it is a really simple install/next/finish type of installation.

I also tried to use ready made virtual appliance from Bitnami, [http://bitnami.org/stack/knowledgetree](http://bitnami.org/stack/knowledgetree)
That's great if you want to test drive software without installing and tampering the system.

---

### Post by janarene on 2008-02-16
I did end up finding an article that applied to this problem.  For those interested in pursuing it, look at [http://www.howtoforge.com/knowledge-tree-document-management-system-on-ubuntu-7.10]("http://www.howtoforge.com/knowledge-tree-document-management-system-on-ubuntu-7.10")

As I mentioned before, I ended up abandoning this idea so I never tried it according to this other articles instructions..   Best of luck to whoever tries this.

---

### Post by moloth on 2008-02-28
The synaptic edition is old too... download the community version:

[http://www.knowledgetree.com/products/opensource/downloadopensource](http://www.knowledgetree.com/products/opensource/downloadopensource)

1. Download the linux stack (125meg or so)
    then it will open firefox and point you to [http://127.0.0.1:8080/login.php](http://127.0.0.1:8080/login.php)
2. login with u: admin p: admin

That simple!

---

### Post by zazuge on 2008-05-13
> The synaptic edition is old too
No it's not just old it's broken
if you want to install knowledgetree go to their website download the stack installation if you want it the easy way
but the stack installation binay is huge and it installs other apps that you have already (MySQL,OpenOffice,Apache....)
so i preffer the source install, but be warned that it's veryhard to do it.
I already installed knowledgtree manually so if anyone wnat help i'm ready.

---

