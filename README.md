# dns-bl-lookup
DNSBL - IP Check

version: 1                
date: 01.06.2016 
Author: Tomasz@Oleksiewicz.pl 
Licence: GNU                                   
Copyright (C) 1999-2016 Tomasz@Oleksiewicz.pl  

This program is distributed in the hope that it will be useful, 
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.


CAUTION:
This is very first version 
1. developed and run only on Centos 6.5
2. using cron mechanism that sends messages to the root if any
3. in the case of multiple IP and many DNSBL the script can work long hours


CONFIGURATION:
1. Configure your network to check. In array $ip_list add IPs or pools. 
   Pools are configured as array('from'=>'0.0.0.1', 'to'=>'0.0.0.254')
2. Check $dnsbl_list 
3. If PING technology is used, check used port list in $ping_list




INSTALLATION:
as root put dns-bl-lookup.php file in /etc/cron.daily/ 
and chmod +x dns-bl-lookup.php 
OR
place  file in /usr/local/sbin/
and write in /etc/crontab 

   25 3,15 * * * root lockfile -r 0 /tmp/.dns-bl-lookup.lock && (/usr/bin/php /usr/local/sbin/dns-bl-lookup.php && rm -rf /tmp/.dns-bl-lookup.lock) 

cron will send to root some raports, also insert your e-mail into /root/.forward to see results in your mail



TODO:
	1. DOMAIN (not IP) blacklist check
	2. WHITELIST IP check (LHSBL) [http://www.blacklistalert.org/]
	3. RFC list check (RHSBL) [http://www.blacklistalert.org/]
	4. SERVFAIL checking
  5. LOCKFILE
  6. IGNORE list
	7. CLI debug, CLI progressbar, counters dnsbl's total, ip's total, ip's/sec, checks/sec  
	8. Quarantine fo SERVFAIL dnsbl
	9. INSTALLATION 

DEBUG:
Some additional information available when DEBUG is TRUE


