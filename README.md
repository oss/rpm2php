rpm2php
=======
This takes information about rpms and packages in koji and displays them in a
handy web interface.

Usage
-----
rpm2php can run in two modes: The browser mode, and admin mode. For both modes,
the file `rpm2php/system/application/config/config.php` needs to be configured.

### Browser Mode
This mode is meant for public networks.
The files
```
	rpm2php/login.php \
	rpm2php/logout.php \
	rpm2php/response.php \
	rpm2php/system/application/controllers/act.php \
	rpm2php/system/application/controllers/queue.php \
	rpm2php/system/application/controllers/updatedb.php \
	rpm2php/system/application/views/application/act.php \
	rpm2php/system/application/views/application/queue.php \
	rpm2php/system/application/views/application/updatedb.php \
	rpm2php/system/application/views/application/webshell.php
```
need to be removed from the public directory. 

### Admin Mode
One needs to crate an .htaccess file. See htaccess-example file.
An .htpasswd file needs to be created with `user: log password: out` via
```
	htpasswd -c .htpasswd log
```
Since there is no actualy logging out from Apache authentication,
we fake logging out by logging in as this user.

Finally, symlinks to
```
	/usr/bin/movepackage
	/usr/bin/pullpackage
	/usr/bin/pushpackage
	/usr/bin/populate-rpmfind-db
```
in the webbin directory for webtools (which should be
`/usr/lib64/webtools/webbin/`) to enable managing publish scripts through
the web interface.

Authors
=======
CodeIgniter team:
- http://codeigniter.com/

OSS:
- Kevin Mulvey
- Dave Diffenbaugh
- Naveen Gavini
- Orcan Ogetbil

Copying and License
-------------------
See COPYING and the LICENSE for more info.
