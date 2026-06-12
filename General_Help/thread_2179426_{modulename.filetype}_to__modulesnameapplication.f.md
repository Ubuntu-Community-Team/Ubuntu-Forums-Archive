---
title: "{module::name.filetype} to _modules/name/application.filetype"
date: 2013-10-08
forum: General Help
---

### Post by gurupal_singh on 2013-10-08
```
path      = content.txt
filename  = application
directory = _modules
 
define create
	$(eval from := $(shell echo $$1)) \
	$(eval to   := $(shell echo $$2)) \
	sed -i '' 's/$(from)/$(to)/g' content.txt
endef
 
all:
	clear
 
	$(eval modules := $(shell egrep -o "{module[^ ]+\}" $(path)))
 
	@for m in $(modules); do \
		$(call create, $$m, \
			$$m \
			| sed 's/{module\([^ ]*\).*}/\1/' \
			| sed 's/\./\/$(filename)\./g' \
			| sed 's/\::/\$(directory)\//g' \
		); \
	done
```



I'm getting this error:
sed: first RE may not be empty

I think the reason for it is because I can not use shell script inside of a for loop because $$1 is returning null.
Anyone have any idea how to solve this issue?
 		 	 		 		 		 		 		 		[HR][/HR] 		[TABLE="width: 100%"]
 		  [TR]
 			[TD="align: left"] 								 			
[/TD]
 			[TD="align: right"] 				[RIGHT] 					 					 					 					 						[[IMG]http://images.devshed.com/fds/buttons/reply_small.gif[/IMG]]("http://forums.devshed.com/newreply.php?do=newreply&p=2893314")[/RIGHT]
[/TD]
[/TR]
[/TABLE]

---

### Post by heir4c on 2013-10-08
I find this:
[http://www.unix.com/shell-programming-scripting/231959-change-everything-file-maps-module-name-filetype-_modules-name-applicat.html](http://www.unix.com/shell-programming-scripting/231959-change-everything-file-maps-module-name-filetype-_modules-name-applicat.html)

---

