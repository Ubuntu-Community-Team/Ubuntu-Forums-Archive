---
title: "Bizarre Virtual Host behaviour"
date: 2007-05-26
forum: General Help
---

### Post by SteveHillier on 2007-05-26
Sorry to bug everyone again.  I don't know how many morehours I can put into this and remain sane.
Surely it is dead simple to set up virtual hosts - or so all the docs and link would tell you.
I have posted other isues and can now get sites hosted.  I started this on Dapper.  When my machine crashed I rebuilt with Edgy and got both my sites working (see below) on my server machine but because of Samba unreliability I could not get my Win 2003 server to see the Edgy machine. I have now reverted to Dapper.
I set up /etc/hosts to have the names of the servers I am hosting on 192.168.0.201 (the IP of my server).  I have in /etc/apache2/sites-available three files --> default, hillierconsult.co.uk (my intranet if it works) and manorind.co.uk (a client site I am testing)  I have done an a2ensite to make sure both sites are listed in /etc/apache2/sites-anabled.  I can get both sites up in Firefox on occasions.
I have now set up my Win 2003 server DNS to recognise the servers hillierconsult.co.uk with an alias of [www.hillierconsult.co.uk](www.hillierconsult.co.uk) and manorind.co.uk with its alias of [www.manorind.co.uk](www.manorind.co.uk).
From my Windows workstation I can access pages correctly from manorind.co.uk, [www.hillierconsult.co.uk](www.hillierconsult.co.uk) and [www.manorind.co.uk](www.manorind.co.uk) but if I try to get hillierconsult.co.uk to work I get the apache default page.  On my Dapper Apache server machine manorind.co.uk works OK.  both www.'server'.co.uk options do not look locally even though the Virtual host files both have a ServerAlias line www.'server'.co.uk in them.  hillierconsult.co.uk gives me apache default page.
Both Virtual Host files have the same construct so I do not know why they behave differently.  The fact that I can access the hillierconsult.co.uk pages from its alias in Windows would suggest it is not the file that is at fault but I may stand corrected.
I have aged 10 years in the last week whilst setting this up.

Virtual host file hillierconsult.co.uk

# NameVirtualHost *

<VirtualHost *>
	DocumentRoot /var/www/hillierconsult
	ServerName hillierconsult.co.uk

	ServerAlias [www.hillierconsult.co.uk](www.hillierconsult.co.uk)
        ServerAlias intranet
        ServerAlias hcintranet
	DirectoryIndex index.php index.html index.htm
	ErrorLog /var/log/apache2/hillier-error.log
	TransferLog /var/log/apache2/hillier-access.log

	<Directory /var/www/>
		AllowOverride None
		Allow from all
	</Directory>

	<Directory /var/www/hillierconsult/>
		AllowOverride None
		Allow from all
	</Directory>

</VirtualHost>

Virtual host file manorind.co.uk

# NameVirtualHost *

<VirtualHost *>
	DocumentRoot /var/www/manor
	ServerName manorind.co.uk
	ServerAlias [www.manorind.co.uk](www.manorind.co.uk)
	DirectoryIndex index.php index.html index.htm
	ErrorLog /var/log/apache2/manor-error.log
	TransferLog /var/log/apache2/manor-access.log

	<Directory /var/www/>
		AllowOverride None
		Allow from all
	</Directory>

	<Directory /var/www/manor/>
		AllowOverride None
		Allow from all
	</Directory>

</VirtualHost>

Any help appreciated
Steve

---

### Post by aceghostwind on 2007-05-28
I had the same problem today and sorted by doing the following.
I was using webmin which so i did not see the warnings when i restarted apache2.
in the default file make sure /etc/apache2/sites-available/default has this entry with your servers ip address in it
NameVirtualHost x.x.x.x


then in the other files in /etc/apache2/sites-available/ replace
<VirtualHost *> with <VirtualHost x.x.x.x>

then restart apache2 with
/etc/init.d/apache2 restart 

Good luck Colin:D

---

