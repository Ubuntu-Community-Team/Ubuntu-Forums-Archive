---
title: "Creating an apache web server"
date: 2008-07-07
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-07-07
Hi
I'm in need of some help with regards to creating an apache web server for open kiosk. This is the readme that I'm trying to follow:
> What is JNodeView
-----------------
JNodeView is a Java applet for viewing the status of an OpenKiosk network from
a remote location. It is platform-independent and designed to be remotely 
viewable from any Java2-enabled web browsers. 

Running JNodeView hosted on a standalone Web server
---------------------------------------------------
JNodeView must be installed under a fully-functional HTTP server such as 
Apache or IIS.  Due to the Java security restrictions, it is required that the 
web server should be on the same machine which is running the NodeView
server. To install JNodeView, simply copy the .jar files in this directory 
into a directory that is made public by the web server. Also, an HTML page 
should be created which will act as a the base document for the viewer applet.
In this HTML page, you should set the applet parameter KLP_PORT to the value
set as the report web server in the Networking and Views page settings of
NodeView. 
See example index.html in this directory using a text editor.

How JNodeView works
-------------------
JNodeView obtains the necessary information from the running NodeView server by
using the XML-RPC protocol. 

Again it must be emphasized that NodeView and the web server serving JNodeView 
must be both running on the same machine.

Diagram:
	   
	 --------------------------------------------
	|			  -----------------  |
	|			 |Apache Web Server| |
	|    ----------		  -----------------  |
	|   | NodeView | <-----	 |    JNodeView    | |
	|    ----------		  -----------------  |
	|				  ^	     |	
	 ---------------------------------|----------
					  |
					  |
					  |
					  |
			     Java2-enabled web browser

How to use JNodeView
--------------------
Your web browser should support applets written in Java2. Get the applet plugin
from [www.java.com](www.java.com) if it does yet support Java2.
Point your web browser to the address of the web server plus path where you 
installed JNodeView. It should initially display the authentication dialog. 
Standard operators and the administrator can use the interface.
JNodeView displays the workstation information in workgroups under a list view.
The view refreshes every 30 seconds. Click refresh if you want to update the 
information that is displayed right away.

Example:

Apache has the document root set at /var/www/htdocs.
JNodeView is installed in /var/www/htdocs/jnodeview

Address of JNodeView is [http://yourserverip/jnodeview](http://yourserverip/jnodeview)

---

### Post by CommonClone on 2008-07-07
The easiest way to set up an Apache web server is to go [here]("http://www.apachefriends.org/en/xampp-linux.html") and follow the instructions.  But you must also follow their instructions to make your server secure if it will be accessible from the internet.

However, you may just want to buy a domain and disk space from a web hosting provider, and install the program on there.  That would seem far easier than dedicating a computer for your website.

---

