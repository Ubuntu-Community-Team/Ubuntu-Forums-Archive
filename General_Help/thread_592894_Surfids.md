---
title: "Surfids"
date: 2007-10-26
forum: General Help
---

### Post by Angryninja on 2007-10-26
Hello,

Has anyone had any luck getting this to run, I'm pretty sure I have configured everything correct, but I cant access the web frontend on the local host. When I go to access the webfront end all I get is the defualt apache 2 screen that says "It Works!"?

Heres a link to the site, pretty sweet look IDS
[http://ids.surfnet.nl/wiki/doku.php?id=home](http://ids.surfnet.nl/wiki/doku.php?id=home)

root@Demonbox:/# cd /tmp/opt/surfnetids/
root@Demonbox:/tmp/opt/surfnetids# ./install_log.pl
Creating /etc/surfnetids/: [OK]
Creating /opt/surfnetids/: [OK]
Copying surfnetids files: [OK]
Adding crontab rule for stat_generator.pl: [info]
Adding crontab rule for mailreporter.pl: [info]
Restarting cron: [OK]

Which apache are you using [apache/apache2/apache-ssl]?: apache2
Setting up apache2 configuration: [OK]
Restarting the apache2 server: [OK]

Do you want to install the database? [y/n]: y
Enter the connecting database user [postgres]:
Enter the IP address of the database host [localhost]:
Enter the connection port of the database host [5432]:
Enter the name of the database [idsserver]:
Enter the name of the web user [idslog]:

Creating SURFnet IDS database [idsserver]: [OK]

Creating webinterface database user [idslog]: [info]
Enter password for new role:
Enter it again:
Creating webinterface database user [idslog]: [OK]

Creating nepenthes database user [nepenthes]: [info]
Enter password for new role:
Enter it again:
Creating nepenthes database user [nepenthes]: [OK]

Creating p0f database user [pofuser]: [info]
Enter password for new role:
Enter it again:
Creating p0f database user [pofuser]: [OK]

Creating SURFnet IDS tables: [OK]

Honeypot FQDN or IP (example: test.domain.nl): 192.168.10.2
Server hostname/IP address: [192.168.10.2]
Is this correct? [y/n]: y

Adding necessary records to the database: [OK]

Do you want to install the nepenthes SQL functions? [Y/n]: y
Installing the nepenthes SQL functions: [OK]

You are currently installing the SURFnet IDS logging package.
This package can be used for a single sensor setup or a multi
sensor setup. If you're not planning on using the SURFnet IDS
tunnel package, choose single sensor setup.

Single or multi sensor setup? [single/multi]: single
SURFnet IDS setup: [single]
Do you want to add your main interface as a sensor? [y/n]: y
Enter the IP address where Nepenthes is listening on: 75.x.x.x <-------------------edited out but my eth0 IP
Adding necessary records to the database: [OK]

Do you want to download the latest GeoIP database? [y/n]: y
Downloading GeoIP database: [info]
--15:52:50-- [http://www.maxmind.com/download/geoi...iteCity.dat.gz](http://www.maxmind.com/download/geoi...iteCity.dat.gz)
=> `/opt/surfnetids/GeoLiteCity.dat.gz'
Resolving [www.maxmind.com](www.maxmind.com)... 67.15.94.80
Connecting to www.maxmind.com|67.15.94.80|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16,469,535 (16M) [application/x-gzip]

100%[================================================== =====================>] 16,469,535 142.08K/s ETA 00:00

15:54:53 (131.54 KB/s) - `/opt/surfnetids/GeoLiteCity.dat.gz' saved [16469535/16469535]


Unzipping GeoIP database: [OK]
Installing GeoIP database: [OK]
Cleaning up the temporary files: [OK]
Building surfnetids-log.conf configuration file: [OK]

#####################################
# SURFnet IDS installation complete #
#####################################

Interesting configuration files:
/etc/crontab
apache2 config files

Still needs configuration:
/etc/surfnetids/surfnetids-log.conf







__________________________________________________ ____
Config


# SURF IDS Options #
####################
# The root directory for the SURF IDS files (no trailing forward slash).
$c_surfidsdir = "/opt/surfnetids";

#######################
# Database connection #
#######################

# User info for the logging user in the postgresql database
$c_pgsql_pass = "";
$c_pgsql_user = "idslog";

# Postgresql database info
$c_pgsql_host = "localhost";
$c_pgsql_dbname = "idsserver";

# The port number where the postgresql database is running on.
$c_pgsql_port = "5432";

# Connection string used by the perl scripts.
$c_dsn = "DBI:Pg:dbname=$c_pgsql_dbname;host=$c_pgsql_host; port=$c_pgsql_port";

################
# Webinterface #
################
# The version of the webinterface.
$c_version = "1.04";

# The port number where apache is running the webinterface on.
$c_web_port = "80";

# Location of the phplot.php library
$c_phplot = "/usr/share/phplot/phplot.php";



There are no pwd on the databases the usernames are correct



Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	apache2-default/	20-Nov-2004 15:16 	-
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 80

tried restarting the datbase as well as the server no luck

---

