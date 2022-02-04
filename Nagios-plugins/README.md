This is a collection of Nagios plugins that I created for my work at SURFsara,
the Dutch national supercomputing center. I think they're far from perfect
and could be easily improved especially regarding portability. I'd welcome contributions.

Onno Zweers


Some usage/troubleshooting hints:
 * Try first to run the script as root and check the output.
 * Do 'su - nagios' and try to run the script as user nagios
   (or user nrpe, in some configurations). Example:
   su - -s /bin/bash nagios -c "/usr/lib64/nagios/plugins/check_kernel"
   If it fails this step, you may need to do some sudoers modifications.
 * If it works then but doesn't work when called from the NRPE daemon,
   you may need to change the 'requiretty'setting.

Here an example excerpt from /etc/sudoers (adapt to your needs): 


Defaults:nagios !requiretty
Cmnd_Alias	NAGIOS_COMMANDS = /usr/lib64/nagios/plugins/check_yum.bash, \
    /usr/lib64/nagios/plugins/check_md_raid
nagios   ALL=(ALL)  NOPASSWD: NAGIOS_COMMANDS
