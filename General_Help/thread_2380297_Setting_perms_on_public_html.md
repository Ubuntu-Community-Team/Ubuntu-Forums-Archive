---
title: "Setting perms on public_html"
date: 2017-12-15
forum: General Help
---

### Post by m-knichel on 2017-12-15
I have a computer science class and teach simple programming classes. I have a few students that want to work with a php framework (Yii2). I want to set their public_html folders to have them as the owner, and www-data as group (recursively). I know how to do this already with a chown and set the perms with chmod. 

I was reading a bit about setfacl and I think it will do what I need. When working with yii and creating crud files, www-data needs write access to the project folder. I was thinking of using setguid and setfacl like this...

# get started so www-data has appropriate perms
$ sudo chown {username}:www-data -R [COLOR=#000000][FONT=monospace]/home/{username}/public_html
[/FONT][/COLOR]$ sudo chmod 770 -R [COLOR=#000000][FONT=monospace]/home/{username}/public_html 
[/FONT][/COLOR]
# set guid so new files/folders inherit group of public_html
$ sudo chmod g+s -R [COLOR=#000000][FONT=monospace]/home/{username}/public_html
[/FONT][/COLOR]
# create an acl so future files/folders get correct perms [FONT=monospace]
$ sudo setfacl -R -m d:u:{username}:rwx,[/FONT][COLOR=#000000][FONT=monospace]g:www-data:rwx,o::-[/FONT][/COLOR][COLOR=#000000][FONT=monospace]/home/{username}/public_html[/FONT][/COLOR][FONT=monospace] 
[/FONT][COLOR=#000000][FONT=monospace]
[/FONT][/COLOR][COLOR=#000000][FONT=monospace]Is this ok?[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]
Lastly, how do I prevent files from getting the x attribute when they don't need it?

I think I have it...

setfacl -R -m d[/FONT][/COLOR][FONT=monospace]:u:{username}:rwX,[/FONT][COLOR=#000000][FONT=monospace]g:www-data:rwX,o::-[/FONT][/COLOR][COLOR=#000000][FONT=monospace]/home/{username}/public_html
Where X only sets the x if it is a dir.

[/FONT][/COLOR]

---

