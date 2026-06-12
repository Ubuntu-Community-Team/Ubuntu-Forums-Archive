---
title: "Apache2 problem"
date: 2012-11-30
forum: General Help
---

### Post by Waleed2 on 2012-11-30
I have one .htaccess file.Its made by an person and i am sure that 100% it works.I edited the .htaccess directory in apache2 config file to /var/www/site/.There is where my site and .htaccess file is.I allowed the htaccess file in the config file.I changed AllowOverRide None to AllowOverRide all.I just wanted to shorten the urls.I tried everything that i could but didnt worked.Take a look at my htaccess file.

So heres the htaccess file code
php_flag display_errors off 
php_flag log_errors On 
php_value error_log Logs/PHPError.log
php_flag html_errors off
php_flag ignore_repeated_errors off
php_flag ignore_repeated_source off
php_flag report_memleaks on
php_flag track_errors on
php_value docref_root 0
php_value docref_ext 0
php_value error_reporting 6143
php_value log_errors_max_len 0

php_value register_globals 0 
php_value session.auto_start 0 

ServerSignature Off
DefaultLanguage en
AddDefaultCharset UTF-8
AddCharset UTF-8 .css
IndexOptions +FancyIndexing
Options +FollowSymLinks -Indexes -ExecCGI
AddHandler application/x-httpd-php .htm
AddHandler application/x-httpd-php .html

<IfModule mod_expires.c>
       ExpiresActive On
       ExpiresByType image/gif A2592000
       ExpiresByType image/png A2592000
       ExpiresByType image/jpeg A2592000
       ExpiresByType image/x-icon A2592000
       ExpiresByType application/pdf A2592000
       ExpiresByType application/x-javascript A2592000
       ExpiresByType text/plain A2592000
       ExpiresByType text/css A10800
</IfModule>

<IfModule mod_rewrite.c>
       RewriteEngine On
       RewriteRule ^404$ Errors/404.php 
       RewriteRule ^home$ index.php
       RewriteRule ^register$ index.php?page=create-account 
       RewriteRule ^page/([a-zA-Z0-9-]+)$ index.php?page=$1
       RewriteRule ^article/(.*)$ index.php?page=full-article&title=$1
       RewriteRule ^shop$ index.php?page=shop 
       RewriteRule ^serverInfo$ index.php?page=server-info 
       RewriteRule ^register-account$ index.php?page=create-account 
       RewriteRule ^securityTips$ index.php?page=security-tips
       RewriteRule ^gift-shop$ index.php?page=shop-gifts [NC,QSA]
       RewriteRule ^donate-shop$ index.php?page=shop-donates [NC,QSA]
       RewriteRule ^partners$ index.php?page=our-partners
       RewriteRule ^shop/get-points$ index.php?page=get-points
       RewriteRule ^shop/donate/purchase/package/id/([\d]+)/name/(.*)$ index.php?page=confirm-payment&_type=package&package-name=$2&id=$1&shop-type=donate
       RewriteRule ^shop/donate/purchase/item/id/([\d]+)/name/(.*)$ index.php?page=confirm-payment&_type=item&item-name=$2&id=$1&shop-type=donate
       RewriteRule ^shop/gift/purchase/package/id/([\d]+)/name/(.*)$ index.php?page=confirm-payment&_type=package&package-name=$2&id=$1&shop-type=gift
       RewriteRule ^shop/gift/purchase/item/id/([\d]+)/name/(.*)$ index.php?page=confirm-payment&_type=item&item-name=$2&id=$1&shop-type=gift
       RewriteRule ^database-error$ Errors/Database.php [NC]
       RewriteRule ^shop/terms$ index.php?page=purchase-terms [NC,QSA]
       RewriteRule ^shop/buy-points$ index.php?page=buy-points [NC]
       RewriteRule ^panel$ index.php?page=management-panel [NC,QSA]
       RewriteRule ^topKillers$ index.php?page=top-killers [NC,QSA]
       RewriteRule ^panel/characters$ index.php?page=management-panel&action=characters [NC,QSA]
       RewriteRule ^panel/news/(update|delete)/(.*)/(.*)$ index.php?page=management-panel&action=news&_request-action=$1&$2=$3 [NC,QSA]
       RewriteRule ^panel/accounts$ index.php?page=management-panel&action=accounts [NC,QSA]
       RewriteRule ^panel/staffHidden$ index.php?page=management-panel&action=staffHidden [NC,QSA]
       RewriteRule ^panel/pointSalePrices$ index.php?page=management-panel&action=pointSalePrices [NC,QSA]
       RewriteRule ^panel/([a-zA-Z0-9]+)$ index.php?page=management-panel&action=$1
       RewriteRule ^panel/([a-zA-Z0-9]+)/(.*)/(.*)$ index.php?page=management-panel&action=$1&$2=$3
</IfModule>
 
ErrorDocument 403 /404.php
ErrorDocument 500 /404.php

<FilesMatch "\.php$">
    Order Allow,Deny
    Allow from all
</FilesMatch>

<FilesMatch "^(index|check-account|check-character|log-parser|post-image-upload|GiftListener|launcher-news|login-check|get-status|logout|404|Database|register-status|delete-case-attachment|vote-redirect|more-news|GiftHandler|DonateHandler|GiftItemHandler|PaypalObject|DonateListener|MessageHandler)\.php$">
    Order Allow,Deny
    Allow from all
</FilesMatch>

<FilesMatch "\.(txt|sql)$">
    Order Allow,Deny
    Deny from all 
    Satisfy Any
</FilesMatch>

---

### Post by pkadeel on 2012-11-30
What exactly you want to get? short url or something else

It appears that you are doing all this on your local computer. If this is the case and you want short url like "mysite" instead of "localhost/mysitename" then you only need virtual host setup. No editing of apache2.conf or other main configuration files required.

---

