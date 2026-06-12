---
title: "htaccess to fix broken images?"
date: 2007-08-11
forum: General Help
---

### Post by timstl on 2007-08-11
I have a website that I copied to my local machine for development reasons. All of the images on the site point to /images/whatever.jpg. This is a problem, because I have Apache setup to use:

/home/tim/sites/site-name-folder

So to access the site I go to [http://dev/site-name](http://dev/site-name) or externally [http://tim.my-dynamic-url.com/site-name](http://tim.my-dynamic-url.com/site-name). 

Because the site is in a subfolder, all of the images break. We're talking hundreds of images, so I need a solution to fix them. 

Is there a way I can use htaccess, I assume in the root folder (/home/tim/sites), to cause the images to redirect to the proper folder? Or does someone have a better solution? I thought about switching over to subdomains instead of folders like I'm using now, but that would cause problems accessing externally, because I use a dynamic URL with a subdomain, as I said above.

Thanks for the help.

---

### Post by timstl on 2007-08-11
I figured out htaccess. I'll post here incase anyone else has this problem:

# Turn on rewrites.
RewriteEngine on

#LimitInternalRecursion 100
#RewriteCond %{REQUEST_URI} ^/cs/html

# Don't apply to URLs that go to existing files or folders.
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d

# Rewrite all those to insert /folder.
RewriteRule ^(.*) cs/html/$1

---

