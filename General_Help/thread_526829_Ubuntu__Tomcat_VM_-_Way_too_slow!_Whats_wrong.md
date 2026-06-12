---
title: "Ubuntu / Tomcat VM - Way too slow! Whats wrong?"
date: 2007-08-15
forum: General Help
---

### Post by tomdavidson on 2007-08-15
Hello:
I have been trying to build a server appliance to run OpenBravo on.
I have everything there and can open the the application via [http://ipadress:8180/openbravo/](http://ipadress:8180/openbravo/) but it literally takes 5 min for the the log-in page to open and some of the images are never displayed.

The appliance is a vmware image with 2GB ram and I run it via vmware server currently on a dual PIV w/ 4GB ram and scisi hds.

The OS is Ubuntu 7.04 server. I installed vmware tools hoping to use use the host clipboard, but it appears you have to have x for that.
Also installed is PostgreSQL, and Tomcat5.5 and Ant from the Ubuntu repo.
Sun Java6 jdk and jre are installed.

When I install openbravo via their universal install script it detects PostgreSQL, Java and Ant just fine, but when it checks Tomcat it can not verify the version (5.5 recommended).

Im thinking maybe the environment variables are wrong?? /etc/environment didnt do the trick for java and I had to append the bash log in script??????

Or maybe and issue with PostgreSQL user permissions ?? but the home page should load fine right?

any brilliant insights??? pretty please??
best regards, tom

---

### Post by Skardal on 2007-08-30
You should make sure that Tomcat really IS using Sun's VM to run your webapps. I had a similiar problem, and it turned out that this was my problem :)

set your *JAVA_HOME* to the correct path in */etc/default/tomcat5*

E.g mine is *JAVA_HOME=/usr/lib/jvm/java-6-sun/*

---

### Post by nitro_n2o on 2007-08-30
you can also run 
```
sudo update-alternatives --config java
``` it'll show a list of java vms you have and you need to type in the right number

---

### Post by jpabloae on 2007-10-20
Hi tomdavidson,

Probably there's a name resolution problem. If one installs openbravo specifying "localhost" as the host name, then there may be problem accessing with the local ip address.
That is, to access openbravo with "http://ipadress:8180/openbravo/" , one must follow one the following paths:

1. Install Openbravo specifying that ip address as the host name (and not localhost). And then access Openbravo using always that ip address.
2. Tweak Openbravo so that it uses relative paths to look for images, js and css files. This way you can access it as you prefer.

In your current situation option 2 looks reasonable. It requires some operations, listed as follows:

[LIST=1]
[*] Go to the AppsOpenbravo directory, and there edit the build.xml file. Fine this line:

```
<property name="web.url" value="http://ipadress:8180/openbravo/web">
```
And replace it with:

```
<property name="web.url" value="../web">
```
Save the file and return to a command line.

[*] Go to the AppsOpenbravo directory and type the following:

```
ant compile -Dtab=xx war
```
This will regenerate the a new war file with the change setting. It takes around 1 minute.

[*] Stop Tomcat, delete /var/lib/tomcat5.5/openbravo and /var/lib/tomcat5.5/openbravo.war and copy AppsOpenbravo/lib/openbravo.war into /var/lib/tomcat5.5/ . And start Tomcat.
[/LIST]

And that's all.

Hope it helps.

---

