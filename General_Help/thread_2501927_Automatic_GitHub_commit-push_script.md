---
title: "Automatic GitHub commit-push script"
date: 2024-10-26
forum: General Help
---

### Post by devpmgeo on 2024-10-26
Hello!

I am fairly new to the ecosystem and discovering scripting to reduce friction of maintenance. I am looking to have a folder that sits on my desktop and containing my work files to be automatically pushed to GitHub every night after work so I get version control and automatic push online of my work data.
The idea would be to have a script running with cron every night at some specific time checking if there is a diff and if so to commit with the date as commit message and automatically push.

Is this a good idea? I've checked phind AI to do the script for me and got the following result:
```
#!/bin/bash

# Set variables
REPO_PATH="/path/to/your/work/files"
GIT_USER="your-github-username"
GIT_EMAIL="your-email@example.com"


# Change to the repository directory
cd "$REPO_PATH"


# Check if there are changes
if git status --porcelain | grep -q .; then
    # Get the current date for the commit message
    COMMIT_MSG=$(date +"%Y-%m-%d %H:%M:%S")


    # Stage all changes
    git add .


    # Commit the changes with the current date as the commit message
    git commit -m "$COMMIT_MSG"


    # Push the changes to GitHub
    git push origin master


    echo "Changes pushed successfully at $(date)"
else
    echo "No changes detected."
fi



```

Then making the script executable 
```
chmod +x auto_push.sh

```

And finally setting up the cron job

```
crontab -e


```

and ```
0 0 * * * /path/to/auto_push.sh >> /path/to/logfile.log 2>&1


```

Does that seem correct? I'm a bit afraid of meddling with things I don't know but willing to learn!

Thanks!

---

