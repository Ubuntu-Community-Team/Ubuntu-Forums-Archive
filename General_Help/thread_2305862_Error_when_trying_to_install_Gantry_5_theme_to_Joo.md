---
title: "Error when trying to install Gantry 5 theme to Joomla on Ubuntu"
date: 2015-12-09
forum: General Help
---

### Post by allstarrunner on 2015-12-09
Hi, and thanks for any help you can give. I installed the Gantry 5 framework no problem into Joomla! (using "Upload Package File"), then I tried to install the theme for it and I received this error:

'/opt/bitnami/apps/joomla/htdocs/templates/g5_hydrogen/custom/config/default' failed on error mkdir(): Permission denied

Clearly it is some sort of permission issue; I'm new to ubuntu, so I could really use some help!

Currently, there is no directory past the /templates/ directory. Joomla is trying to create those directories and put the files into them. So the only thing that exists right now is /opt/bitnami/apps/joomla/htdocs/templates

I tried to create the folders myself, and the re-install it, but I still go the same error because I think it still wants to create those folders on its own.

someone else had me do this:
'cd /opt/bitnami/apps/joomla && chmod -R g+w htdocs/'
but to no avail.

edit: this is what I get up to the templates directory:
total 16
drwxrwxr-x 7 bitnami daemon 4096 Nov 17 10:36 beez3
-rw-rw-r-- 1 bitnami daemon 31 Oct 21 17:48 index.html
drwxrwxr-x 9 bitnami daemon 4096 Nov 17 10:36 protostar
drwxrwxr-x 5 bitnami daemon 4096 Nov 17 10:36 system

edit 2: also, i'm running this on a virtual machine through AWS so the permissions are setup however they decided to do it; they said in the documentation that I am by default not a root user, but to run sudo to gain that capability; the problem here is that I'm not running the command myself and able to use sudo, I think that is where part of the problem is coming in.

edit 3: looking on forums to a problem similar to mine, I tried doing this:
sudo chown -R bitnami:daemon htdocs
I tried to reinstall the theme, and this time I got a different error:
Opening file for writing failed on error fopen(/opt/bitnami/apps/joomla/htdocs/cache/gantry5/g5_hydrogen/compiled/yaml/8a145b5685984bd7844497977c280db1.yaml.php): failed to open stream: Permission denied

not sure if I just took a step forward or backward...

---

