---
title: "mysql :: user privilege corruption forcing --skip-grant-tables"
date: 2008-03-20
forum: General Help
---

### Post by bowmanr on 2008-03-20
good day,

posted this on the mysql forums, no response, wondering if anyone here has got a clue please ...

<previouspost>
good day,

a question from a complete mysql newbie here.

my server running mysql (linux, ubuntu, fiesty) experienced a brownout which had rather a negative impact on my user rights system table. now, i can only run the mysq daemon with 'mysqld --skip-grant-tables &'. this i've added to rc.local. not an ideal solution really.

is there anyway to force mysql to rebuild the user rights system table?

on a completely different machine, i tried installing mysql-server, setting the root password to something specifc, and then purging the mysql install with 'sudo aptitude purge mysql-server'. however, when i subsequently reinstalled mysql-server, the root password remained as per the previous install. i therefore infer from this that a simple remove and reinstall won't necessarily fix the corruption. maybe someone could let me know what else i need to manually remove between the purge and install commands?

thanks for any thoughts and advice
robert bowman
</previouspost>

the following link i found has been helpfull : [http://bookmarks.honewatson.com/2008...-feisty-gutsy/](http://bookmarks.honewatson.com/2008...-feisty-gutsy/)

from the info in the above link, i've written a script which will dump databases, purge mysql-server, reinstall mysql, rebuild database. this script successfully resolves the issue on a test box under gutsy. however, on the live server, the "sudo apt-get –purge remove mysql-server mysql-common mysql-client" command insists on removing additional software which is dependent on mysql. a reasonable thing todo, certainly ... however, i REALLY do not want to have to reinstall everything else again! arrrgh! i changed apt-get to aptitude and discovered the gui which allows selection of removals, but it kept mentioning downgrading packages etc...

can i prevent this behaviour please? is it possible to remove mysql-server and it's dependencies, but not remove ANYTHING dependent on mysql-server. therefore, keeping the server in it's current software configured state post the reinstall and fix to mysql???

or alternatively, can anyone think of a way of acheiving part one of what i posted to mysql -- in essence "how can i force a rebuild of the system database responsible for user privileges?".

thanks for your thoughts
robert

---

### Post by bowmanr on 2008-03-20
if it helps, i've just taken the attached screenshot of mysql-admin looking at the mysql schema. not sure i like the look of them 'Incorrect file format' messages!!

any thoughts please?
robert

---

### Post by bowmanr on 2008-04-17
well, i eventually got motivated to really get into this and work out how to fix it. success.

so, just in case, one day, someone has a blown mysql install which forces running in '--skip-grant-tables' mode, here's what i had to to.

simply put : use a second install of mysql on an alternate ubuntu box. configure it such as the blown mysql install should be. copy the 'mysql' schema files and also the credential files which allows debian maintenance tasks.

further details :

Notes :
	Hostnames are 'second' for machine in working state, and 'broken' for the broken box

step 1] on second box, backup current configuration :
	second# cd /var/lib/mysql
	second# sudo mkdir mysql.KEEP_SAFE
	second# sudo cp mysql/* mysql.KEEP_SAFE/
	
step 2] configure second box accordingly 

step 3] prepare broken machine for files (create /home/<SOMEUSER>/tmp/repairMYSQL with subfolders 'mysql' and 'config'

step 4] get this config across to the broken machine :
	second# cd /var/lib/mysql/mysql
	second# scp * <SOMEUSER>@broken:/home/<SOMEUSER>/tmp/repairMYSQL/mysql
	second# cd /etc/mysql
	second# scp debian.cnf <SOMEUSER>@broken:/home/<SOMEUSER>/tmp/repairMYSQL/config

step 5] revert second box to good state
	second# cd /var/lib/mysql/mysql
	second# sudo rm *
	second# sudo cp ../mysql.KEEP_SAFE/* .

step 6] stop mysql on the broken machine
	broken# sudo /etc/init.d/mysql stop

step 7] cache current broken state (just in case!)
	broken# cd /var/lib/mysql
	broken# sudo mkdir mysql.BROKEN_USER_PRIVS
	broken# sudo cp mysql/* mysql.BROKEN_USER_PRIVS/
	broken# cd /etc/mysql
	broken# sudo cp debian.cnf debian.cnf.BROKEN_USER_PRIVS

step 8] copy in the good configuration
	broken# cd /var/lib/mysql/mysql
	broken# sudo rm *
	broken# sudo cp /home/<SOMEUSER>/tmp/repairMYSQL/mysql/* .
	broken# cd /etc/mysql
	broken# sudo cp /home/<SOMEUSER>/tmp/repairMYSQL/config/debian.cnf .

step 9] restart mysql
	broken# sudo /etc/init.d/mysql start

hope for the best

ok, we've now got both machines with identical debin system maintenance properties. personally, i don't care. you may though. i tried doing with with some GRANTs on the new mysql database maintenance account according to the original debian.cnf. i failed. i could not be bothered to track it down any further and accepted the duplicate account settings.

the steps above kind'a describe the process, but i'm not at the machines now and at work, using windows XP so can't check paths. all from memory. so, you're gonna need to have a rough idea of what you're doing before attempting this.

hope that one day these rough rambling thoughts help someone else in the same hole i was in for several months

all the best
robert

---

