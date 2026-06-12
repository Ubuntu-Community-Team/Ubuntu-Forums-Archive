---
title: "php5 readdir() problem"
date: 2007-04-28
forum: General Help
---

### Post by howlingmadhowie on 2007-04-28
hi. i'm having a problem with the readdir() function in the version of php5 in the repositories:

[INDENT]function makeNavigation($input)
{
	echo "<table id=\"navigation\">\n";
	$dir=opendir('./pages');
	if($dir)
	{
		while($file=readdir($dir));
		{
			echo "bin im loop: ".$file;
			if(is_file($file))
			{
				echo "<tr><td style=\"file\">".$file."</td></tr>";
			}
		}
		closedir($dir);
	}
	else
	{
		echo "<tr><td>konnte ./pages nicht &ouml;ffnen</td></tr>";
	}
	echo "</table>";
}[/INDENT]

returns: 
[INDENT]<table id="navigation">
bin im loop: </table>[/INDENT]

although ls -l pages returns:
[INDENT]ls -l pages
total 4
-rw-r--r-- 1 anton anton 151 2007-04-27 22:13 main.html
-rw-r--r-- 1 anton anton   0 2007-04-28 20:20 testfile.txt
[/INDENT]

is this a bug in php5? i get the same lack of a result on the command-line as over the apache server.

-------------------------------

(edit)

sorry, my bad :)

boy, is this embarrassing...

---

