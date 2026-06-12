---
title: "web based inventory control software"
date: 2007-07-23
forum: General Help
---

### Post by loserboy on 2007-07-23
I just downloaded this [http://linux.softpedia.com/get/Information-Management/Inventory-Management-Software-2821.shtml](http://linux.softpedia.com/get/Information-Management/Inventory-Management-Software-2821.shtml)

and I have no idea how to get it working.

It's suppose to be a simple web based inventory program

-From the readme-

installation:
-copy all files to your web host
-use phpmyadmin or your mysql interface to run site.sql to setup your database.
-open site.xml and edit the database section with your database details.
-go to index.php and login with username of admin with a password of test.
-be sure to change the passwords for the admin and regular user.

To change the title of the system edit line 8 of
templates\admin\layout.htm between the <title> tags.

Setup the site.xml file with your database settings as follows.

<database type="mysql">
   <server>database server address</server>
   <login>database login</login>
   <password>database password</password>
   <default>mysql database name</default>
</database>
-----------------------


I have a site the can host the software, that much I know. 
The site has a control panel where I can login into phpmyadmin, but I know nothing about that or mysql.

any help would be appreciated, thanks

---

### Post by HermanAB on 2007-07-23
You could also look around for a VMware appliance.  Then you only need to install VMware and getting the preconfigured 'appliance' going is really easy.  Start by looking on the VMware web site - they have a whole zoo there.

Cheers,

Herman

---

### Post by loserboy on 2007-07-24
thanks and I'll look into that, but I was really hoping to get this going, it seems so easy, but just out of my reach

---

### Post by loserboy on 2007-07-25
one bump before I let it go... I'd pay to get this working

---

### Post by OffAxis on 2007-07-25
So you can get into phpmyadmin without an issue?

**Database Creation**
Once you're in with phpmyadmin create a new database (the first text box on the home page there) and call it 
**inventory**

Hit the 'Go' button, and it'll tell you that it's been created, but there are no tables. That's fine.
Next, on to the 
**Import **tab. Search for the file on your local machine (**site.sql**), accept the defaults, and hit the 'Go' button again. It should create a number of tables for you (7).
Almost done with the database setup.
On to the **Privileges **tab.

This is a listing of every account that has access to this new database. You can use one or two of these existing accounts if you want (usually an administrator account and a restricted user account) OR you can create new accounts.

**Creating New Accounts**
Click the Home Icon on the far left. 
Click **Privileges **in the left column.
Click 'Create New User'.
   Create a name/password. No need for any privileges (yet). Click Go.
Now, the 2nd block down the page is for 'Database Specific Privileges'. Select '**inventory**' from the drop down list box and hit go.
Set it up however you want (probably just the 4 under 'data' is sufficient for an ordinary account)

Does that help?

---

### Post by loserboy on 2007-07-26
I can get into phpmyadmin without issue but it won't let me make a new database, it says in red no priviliges, could it be it takes some time to be updated since I just made a account and stuff

---

### Post by loserboy on 2007-07-26
just checked and it still won't allow me to make a database.

I go through a control panel that the website host has, called database manager and I actually created a database the a username and pass there, could that have something to do with it?

edit: ok I googled it, my host only allows so many accounts and I have to do it through their control panel, and there is no privileges tab.

which brings me to the question - do I just forget about these steps?

> 
Creating New Accounts
Click the Home Icon on the far left.
Click Privileges in the left column.
Click 'Create New User'.
Create a name/password. No need for any privileges (yet). Click Go.
Now, the 2nd block down the page is for 'Database Specific Privileges'. Select 'inventory' from the drop down list box and hit go.
Set it up however you want (probably just the 4 under 'data' is sufficient for an ordinary account)

---

### Post by OffAxis on 2007-07-26
ya, what's important is

1. database named **inventory**
2. username with typical user access (select, update, insert, delete) to that database

have you gotten that far?

---

### Post by loserboy on 2007-07-26
thanks so much for your help so far.

well I actually named it inventory3 because of some previous failed attempts to make a database and even though I deleted them for some reason it won't let me make a new one just called inventory.

I do have the user, I don't see where the control panel will let me choose what it can do so I assume it's an administrator (which is fine with me if it is ok)


I also imported the the site.sql and I see 7 tables, under the collation column it says they are "latin1_swedish_ci"  is that ok

---

### Post by OffAxis on 2007-07-26
yes, latin1_swedish_ci is okay.

Generally, you want to run the site through as limited an account as you can get away with. For example, the limited user (select, delete, update, insert) can't affect the structure of the database or tables, while an administrator account can wipe out tables or the entire db easily, so if the account you're using is compromised, (through a visible site.xml file in this case) you don't lose everything due to a malicious user.

For testing you can get away with it, but in a 'live' situation where you're depending on the data I'd really get that limited account in place.


I only emphasized the name inventory because that's how the .sql file was set up. Since you've already used that file to build the tables in the database, then you're fine.

So, all that remains is:

1. modify the site.xml file for the appropriate user name, password, and database name (in the **<database type="mysql"> **section)
2. modify the .htaccess with the 
[B]</Files ~ ".xml">
Order allow,deny
Deny from all
Satisfy All
</Files>
[/B]
specification.

After that, you should be able to log in (at http://yoursite.com/relativepath/index.php) with a name of **admin **and a password of **test**.

---

### Post by loserboy on 2007-07-26
ill call up support and they'll tell me how to fix the account, i understand what you're saying I'll just be happy to see it function.

I'll try the other part as soon as this uploads to the site.


edit:i see this -

<database type="mysql">

		<server>localhost</server>

		<login>root</login> <--- myusername here

		<password>cats</password> <---my pasword here

		<default>inventory</default>  <----do i need to rename to "inventory3

	</database>
-----------------------------------------------

> 
2. modify the .htaccess with the
</Files ~ ".xml">
Order allow,deny
Deny from all
Satisfy All
</Files>

sorry do I just append this onto the site.xml?

I couldnt find an .htaccess anywhere

---

### Post by OffAxis on 2007-07-26
Sorry, I should have been clearer about that.

A .htaccess file controls the access that visitors have to files or functions in your website. For instance, from the apache2.conf (Apache 2's configuration file)

[B]<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>[/B]

stops visitors from being able to view a .htaccess file.

These .htaccess files limit access on a PER DIRECTORY basis, so you can have different rules for different folders. 

Anyway, create a text file on your machine called **.htaccess** and paste that section from the readme into it; (theoretically) this section

</Files ~ ".xml">
Order allow,deny
Deny from all
Satisfy All
</Files>

**However**, I think that first line has an error in it. While there are a few different ways of going about writing the access rules, I know this one works (in apache 2, anyway).

[B]<Files ~ "\.xml$">
Order allow,deny
Deny from all
Satisfy All
</Files>[/B]

So save that in your .htaccess file and upload it to the same folder as your inventory scripts (index.php)
Note that any file beginning with a dot (.) is a hidden file. So if you don't see it in your file browser don't worry; it's still there.
From a command line

**ls -a**

or

**ls -a /path/to/folder**

will show all files in a directory

---

### Post by loserboy on 2007-07-26
alrighty I'll try that as soon as I get to work in the morning

---

### Post by OffAxis on 2007-07-27
Cool.
Let me know how it goes.

---

### Post by loserboy on 2007-07-27
I used your version of the htaccess and uploaded it.

when I try to view the page i get this error message

> 
Warning: mysql_connect() [function.mysql-connect]: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2) in /data/13/0/103/63/755715/user/772550/htdocs/Generators/inventory/lib/database.php on line 85

Warning: mysql_error(): supplied argument is not a valid MySQL-Link resource in /data/13/0/103/63/755715/user/772550/htdocs/Generators/inventory/lib/database.php on line 85
CDatabase::Connect() error


edit: this is line 85 of that file if it matters
$this->conn_id = mysql_connect($server,$login,$password,TRUE) or die("CDatabase::Connect() error " . mysql_error($this->conn_id));

---

### Post by OffAxis on 2007-07-27
Just to round out the .htaccess thing...

Try accessing the file site.xml by typing http://yoursite.com/path/site.xml into firefox.
it should come up as forbidden. If it's viewable let me know.

Okay, so it's having an issue with the connection. 
One of the connection variables there in the site.xml file doesn't match up with the settings on the server. It's probably the server name 'localhost'.

Connect to your mysql database with your host's interface software and look for the name of the server host.

It'll be something like **p41mysql71.secureserver.net** (a sub-domain of your actual host is what I'm getting at). 
Change out 'localhost' for that variable and it should work.

---

### Post by loserboy on 2007-07-27
yea the .htaccess worked perfect, i get a forbidden message.


the only thing I can see about the server is "running on localhost as michaelr@localhost

and theres an ip that I can use to go direct to the database, I can post it if you want, I just didn't know if it's ok for everyone to see it

---

### Post by loserboy on 2007-07-27
when I go to database then click the status tab it gives me a not found message but beneath it says
"Apache/1.3.37 Server at mysql3.netsolhost.com"
any chance that could be it or is that for something else

sorry this is taking so long, you have no idea how much i appreciate your help

edit: well I tried mysql3.netsolhost.com and no go

---

### Post by loserboy on 2007-07-27
wohoo!  the ip address worked

---

### Post by OffAxis on 2007-07-27
great!
so you're in!
I'm happy to hear that.

Login is **admin **and password is **test**.


I've also attached a couple files for you. By unzipping these into your site you can try out the different variables involved in a mysql_connect function (on the testlogin.html page). You don't need them now that you've got a good connection, but maybe they'll come in handy sometime. You can try out known good values as well as known bad values and see what kind of error messages you get for the different variables.

---

### Post by loserboy on 2007-07-27
thanks again and I'll play around with the files there.

I do have one last simple question - I ended up making a htaccess.txt and uploading it then removing the .txt and adding the hidden bit, but on my first attempt I made a .htaccess file before uploading and I can't remove it off my desktop.

I tried rm, sudo rm, I tried changing the permissions but my computer doesnt even think it exists, ls -a doesn't show it

---

### Post by OffAxis on 2007-07-27
interesting.

Can you interact with it on the desktop at all graphically? Does a right click on it give you any options?

it could just be a video artifact. Try a logoff and logon and see if it goes away.

If it still remains...

**sudo ls -la /home/yourname/Desktop**

just to see if it's there and if the permissions are funny.

A 

**sudo rm -f .htaccess**

should forcibly remove it.

You could also try moving it with a 
**mv **
command and see if that has any effect.

---

### Post by loserboy on 2007-07-27
a reboot worked, I thought I had refreshed the desktop but I guess it needed more than that

---

