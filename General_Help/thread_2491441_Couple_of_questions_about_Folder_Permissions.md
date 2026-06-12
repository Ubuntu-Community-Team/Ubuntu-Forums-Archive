---
title: "Couple of questions about Folder Permissions"
date: 2023-10-09
forum: General Help
---

### Post by chevv on 2023-10-09
Question 1:
Is it possible to list all the permissions (r, w and x) that a given USER (logged in user or other user) has on a target FOLDER?

Question 2:
Is it possible, for a given FOLDER, to list all the Users and Groups that have a particular permission (say, "execute") on it?

Appreciate any suggestions to help me with this.

---

### Post by yancek on 2023-10-09
Using the command ls -ld /directoryname should show the permissions.  The first set (rwx for example) will be the owner, the second set the group and the third set for others.  The second set would be for any user in the specific group show in the command output.  You can find users in the group with the command:  cat /etc/group which displays a text file listing all groups with users on the line of the particular group.  If this isn't what you are looking for, post back with more specifics.

---

### Post by chevv on 2023-10-09
> **yancek said:**
> Using the command ls -ld /directoryname should show the permissions.  The first set (rwx for example) will be the owner, the second set the group and the third set for others.  The second set would be for any user in the specific group show in the command output.  You can find users in the group with the command:  cat /etc/group which displays a text file listing all groups with users on the line of the particular group.  If this isn't what you are looking for, post back with more specifics.

Thanks for answering, yancek. I follow what you are suggesting but to assess it fully I have a supplementary question:  Is it possible for more than one user group to be given read / write / execution permission on a given folder?

---

### Post by TheFu on 2023-10-09
> **chevv said:**
> Thanks for answering, yancek. I follow what you are suggesting but to assess it fully I have a supplementary question:  Is it possible for more than one user group to be given read / write / execution permission on a given folder?

Yes.  You should spend 45 minutes working through a Unix permissions tutorial and whatever amount of time you need to understand the 3 parts
[LIST]
[*]Owner
[*]Group
[*]Other
[/LIST]

There is only 1 owner. Period. The owner can manage permissions on the file or directory.
There is typically only 1 group.  Members of the group get those permissions. 
Any user who isn't a member of the group or the owner, is "other".  You may see this in some texts as "world", but that is incorrect.  Other DOES NOT include the owner nor members of the group.  So it is possible to setup permissions so a since group cannot access a file, but everyone else on the system can.

Those are the normal ways that permissions are grouped.

There there are ACLs which can break all sorts of rules and are typically not used.  In 30 yrs as a Unix admin, I've needed to use ACLs just twice.  I've come across them about 10 times, usually by lazy people who don't really understand permissions. Best to avoid/ignore them for now. It is unlikely you'll see ACLs used.  ACLs aren't available for all file systems, but they are mostly enabled on native linux file systems.  It is possible to have ACLs completely override what the normal POSIX permissions with the **ls -l** command shows.  If you want to be an evil system administrator, you can screw with end-users that way. It can be fun, in an evil way.

To see groups for a specific userid, there is the 'groups' command.  Also, you can use the 'id' command for any user to know which groups of which they are a member.

Anyway, find a tutorial. WORK through it, don't just read it. That should be about 15 minutes.
Then create 3 temporary accounts and some temporary directories under /tmp/foo/   , then setup the owner and groups in a mix and match way so that 2 users are in the same group and one is not.  Then test out files and directories with every possible combination of permissions. Starting with 000, 100, 200, 300, 400 ..... 777. Permissions are octal (0-7). See what each user can and can't read, can and can't write, and if there is a tiny script, which they can and connect run.  By the end of this, you'll have memories the most common octal patterns and be able to easily read the output from 
**ls -al** on any directory or file.

These permissions are the core of all Unix system security, so spend the time to learn it now and you'll save hours, weeks, months of frustration.

After you get the "click" of understanding, go a few more minutes and verify things work the way you need.  For example I often use 710 permissions for directories when I want someone to run a program, but not have any other access.  They cannot run scripts with those permissions. Why not?

Lastly, you might want to learn some specific directory settings, like the setgid flag on a directory.  That's helpful when different userids need to work in the same directory.  The "sticky bit" isn't all that useful, but /tmp/ has it set for specific reasons.  Why is that?

---

### Post by btindie on 2023-10-09
> You can find users in the group with the command: cat /etc/group
Alternatively you can use the members command from the package with the same name.

> Is it possible for more than one user group to be given read / write / execution permission on a given folder?
Yes, by means of the setfacl command which applies ACLs to files and directories. It allows you to give additional users and groups access. You can also apply default ACLs to directories which then get automatically applied to newly created files. You can view ACLs with the getfacl command and you'll need the acl package installed.
When ACls are applied, the `ls` output includes a '+' at the end of the standard permissions to indicate that it has an ACL applied, as seen in the below example on the home directory
```

drwxr-xr-x    2 root root  4096  1 Oct 00:00 etc
drwxr-x--x+ 208 root root  4096  5 Oct 00:00 home

```
The man page for setfacl has a full set of examples.

---

### Post by Holger_Gehrke on 2023-10-09
> **chevv said:**
> I follow what you are suggesting but to assess it fully I have a supplementary question:  Is it possible for more than one user group to be given read / write / execution permission on a given folder?

To answer that in German: Jein (yes _and_ no).

Using the normal permission model, permissions are stored per file for exactly one user, one group and for all others (meaning not the owning user nor a member of the group).

It is however possible to use POSIX Access Control Lists to assign more complex permissions. ACLs are rarely used because the default tools for file management - whether graphical or on the command line - mostly ignore their existence, so using them carries the risk of finding yourself not seeing all the permissions that are set on a given file or directory. Take a look at the man pages for acl, chacl, getfacl, and setfacl.

Holger

---

### Post by chevv on 2023-10-09
Thanks for the detailed replies, and some welcome bits of free education thrown in. All appreciated.

(Get the gist of setgid but not why scripts are excluded @thefu).

So my conclusion is that, excepting special scenarios (ACLs), linux setups will all have ONE group per folder. Quite a big deal.
Surprising, given most company IT systems routinely permit multiple user groups to access company Data and Functional assets in a privileges matrix.

But, that's not relevant here and leaves me satisfied since one-group-per-folder makes life simpler in tracking permissions.
So, takeaways for my original questions, given the fresh one-group-per-folder insight:

Question 1: Using the ls -ld command, I can easily check what group has permissions to the folder, and then separately check whether the user is a member.

Question 2: Don't yet know an uncomplicated way to discover a simple list of ALL usernames with r/w/x permission on a folder?

---

### Post by MAFoElffen on 2023-10-10
Any time you use an -l flag with ls, it will show long fomrat, which if the file or folder has an ACL attached to it, that will show a "+" at the end of the permissions list, to tell you there is more to that.

Using setacl, you can granually set the ACL of files and directories to alter how other users and groups in the way of access and permissions. getacl will list what those AC:'s are. Here is an example of that:
```

[root@lab1 accounting]setfacl -m kenny:rwx /accounting
[root]getfacl ./
# file: .
# owner: accounting
# group: accounting
user::rwx
user:kenny:rwx

```
This is a good read that expands on that: [https://www.redhat.com/sysadmin/linux-access-control-lists](https://www.redhat.com/sysadmin/linux-access-control-lists)

---

### Post by chevv on 2023-10-10
Thanks for that, think I got all my bases now covered.

---

### Post by TheFu on 2023-10-10
> **chevv said:**
>  
Question 2: Don't yet know an uncomplicated way to discover a simple list of ALL usernames with r/w/x permission on a folder?

None exists, but I suppose you could create a script that does the de-referencing for you.  In general, only 1 "owner" will have rwx.  From time to time, it might be useful to setup specific directories for a team to work inside. Often, a new group will be setup that is specific to that work area. All files under the top directory will be owned by that group and any newly created files will have the same group attached.  Anyone outside the group wouldn't have write access, so it would come down to the owner (who will be a member of the group) and all group members, so only 1 command is needed to see all the members in a traditional setup.
```
$ groups  {groupname}
```

You can find all the files that a specific user or group or both that have specific permissions using the **find** command.  'find' is a non-trivial command, but useful.  Search for _Top 50 Examples of find_ since it is very capable and can be complex.  Look for the *-perm* option.  From the manpage:
```
       -perm mode
              File's  permission  bits  are  exactly mode (octal or symbolic).
              Since an exact match is required, if you want to use  this  form
              for  symbolic  modes,  you  may have to specify a rather complex
              mode string.  For example `-perm  g=w'  will  only  match  files
              which  have  mode 0020 (that is, ones for which group write per&#8208;
              mission is the only permission set).  It is more likely that you
              will want to use the `/' or `-' forms, for example `-perm -g=w',
              which matches any file with group write permission.  See the EX&#8208;
              AMPLES section for some illustrative examples.
```
There are a few more paragraphs for -perm use which are worth reading.  I've used -perm just a few times in my 30 yrs.  I suspect whatever you really need to do has a better solution than what your mind has come up with.  That's common for new people.  

When I was starting, I'd try to come up with steps based on my knowledge of other OSes and tools they provided to accomplish a task.  Then I'd ask about each step one at a time.  Around step 3, someone with lots of experience would ask what my final goal was, which I'd say.  Then they show a 1-2 step solution. My ignorance of available tools was the issue.  OTOH, it got me exposed to some commands that I'd never use.  For example, 'cat' is next to useless, but seems to be used all the time in made up examples. 99.99% of the time, cat isn't needed, since nearly all commands will accept a filename as input instead of needing stdin.  I always say this ... I have 100x more use for **tac** than I do for **cat**.  I used tac last week. Very useful.  The last time I used cat for a non-contrived use was probably 7+ yrs ago.

---

### Post by MAFoElffen on 2023-10-11
> **chevv said:**
> Question 2: Don't yet know an uncomplicated way to discover a simple list of ALL usernames with r/w/x permission on a folder?
Yes. Not "uncomplicated"... Something like this that takes a folder as a parameter and was about 100 lines:
```

#!/bin/bash
## MAFoElffen,<mafoelffen@ubuntu.com>,20231010
# find-folder-rwx-users.sh
#\# Sample parse: drwxr-x--- 23 mafoelffen mafoelffen   41 Oct 10 17:59 .

USERS=()
GROUPS=()
HasAcl=1

#Get a parameter as a directory name
if [ -d $1 ]
then 
  FOLDER=$1
else
  echo -e "Parameter was not a valid folder"
  exit 1
fi

# find owner & owning group
GetFolderInfo=$(ls -ld $FOLDER | awk $1 " " $3 " " $4 ')

EligibleUser=$(awk '/^drwx/ {print $2}' <<< ${GetFolderInfo[0]}) 
EligibleGroup=$(awk 'awk '/^d...rwx/ {print $3}' <<< ${GetFolderInfo[0]}) 
EligiblePublic=$(awk '/^d......rwx/ {print "Everyone"}' <<< ${GetFolderInfo[0]})
HasAcl=$(awk '/^d.........+/ {print "0"})' <<< ${GetFolderInfo[0]}

If [ ! -z $EligiblePublic ]
then 
  echo -e "$EligiblePublic has rwx permissions for $FOLDER"
  exit 0
fi

if [ ! -z $EligibleUser ]
then 
    if [[ "$EligibleUser" == "EligibleGroup" ]]
    then
        USERS+=("$EligibleUser")
    else
        USERS+=("$EligibleUser")
        if [ ! -z $EligibleGroup ]
        then
            GROUPS+=("$EligibleGrouup")  
        fi
    fi
fi 

if [ $HasAcl -eq 0 ]
then 
    AclInfo=$(getfacl -cp | grep -e '^user:.*:rwx' -e '^group:.*:rwx')
    for i in $(AclInfo[@])
    do
        if [[ "user" == "$i"* ]]
        then 
            USERS+=$(awk -f ":" '{print $2}' <<< $i)
        elif [[ "group" == "$i"*  ]]
        then
            GROUPS+=$(awk -f ":" '{print $2}' <<< $i)
        fi
    done  
else 
    # Nothing to add
fi

if [ ${#GROUPS[@]} -eq 0 ]
then
    # Nothing to add
else
    for GROUP in ${GROUPS[@]}
    do
        TmpMembers=$(members $GROUP)
        if [ ! -z TmpMembers ]
        then 
            for member in ${TmpMembers[@]}
            do
                USERS+=$member
            done
        fi
    done
fi

if [ ${#USERS[@]} -eq 0 ]
then
    echo -e "No one has rwx permissions on $FOLDER"
else
    echo -e The following users have rwx permisions on $FOLDER
    for User in ${USERS[@]}
    do
        echo -e "$User"
    done
fi
exit 0

```

---

### Post by yancek on 2023-10-11
> Question 2: Don't yet know an uncomplicated way to discover a simple list of ALL usernames with r/w/x permission on a folder? 				 

The group would need to show rwx permissions so to get the members of the group for a specific directory use the command below, replacing groupname with the actual group name.

> grep 'groupname' /etc/group 

---

### Post by MAFoElffen on 2023-10-11
> **yancek said:**
> The group would need to show rwx permissions so to get the members of the group for a specific directory use the command below, replacing groupname with the actual group name.
Not necessarily... If you do
```

grep 'rwx' /etc/group

```
It will come up empty. In the record layout of that file, between the group name and the 'GUID' of the group, all it has between the colon record separator, is either null or an "x" to indicate if the group can execute things... None of that record field in that file excepts an "r" or "w" as a valid value. So none of those records have rwx, only x or nothing.

In the conditions for permissions on a folder, you look at the permissions of the folder > parse through that for owner and owning group... to check if any of those have rwx. > If it has a"+", then check the ACL's to see if anyone or any other group has rwx, list the members of all the groups that do have that... 

Note: After thought... What the script above didn't do, was to post-process the list of Users as unique Users, so there would be some duplicates in that list. (Dang)

---

### Post by #&amp;thj^% on 2023-10-11
> **TheFu said:**
>   I used tac last week. Very useful.  The last time I used cat for a non-contrived use was probably 7+ yrs ago.
+1 Great Tip!
> **MAFoElffen said:**
> 
 either null or an "x" to indicate if the group can execute things... None of that record field in that file excepts an "r" or "w" as a valid value. So none of those records have rwx, only x or nothing.


Good example shown from another OS:
```
grep 'wheel' /etc/group 
wheel:**[COLOR="#FF0000"]x[/COLOR]**:998:me

```
And for ubuntu:
```
grep 'adm' /etc/group
adm:x:4:syslog,me
lpadmin:x:114:me

```

---

### Post by yancek on 2023-10-12
> grep 'rwx' /etc/group

I'm not sure what the relevance is here as the OP is looking for members of a group and 'rwx' is not a group.  The command I posted (which was new to me) does show members of the specific group.  The ls -ld command shows which group for the directory.  What I understand the OP wants is a command which will show both and I don't know of a way to do this with a single command/script.  To use the grep command one would need to already know the group.  I imagine there is a way to do this but I don't know what it would be.

---

### Post by TheFu on 2023-10-12
> **yancek said:**
> I'm not sure what the relevance is here as the OP is looking for members of a group and 'rwx' is not a group.  The command I posted (which was new to me) does show members of the specific group.  The ls -ld command shows which group for the directory.  What I understand the OP wants is a command which will show both and I don't know of a way to do this with a single command/script.  To use the grep command one would need to already know the group.  I imagine there is a way to do this but I don't know what it would be.

/etc/group isn't the only place where groups are stored.  The safer command would be to use **getent group {groupname}**.  This will honor network/centrally managed users and groups too like LDAP.

---

