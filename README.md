openshift-papertrailapp-cartridge 2
===================================
*(it uses remote_syslog2 from papertrail)*


####This only works on non-scaled gears at the moment

Add an environment variables for your papertrailapp port number and hostname:

    rhc set-env PAPERTRAILAPP_HOST=<host>.papertrailapp.com -a <appname>
    rhc set-env PAPERTRAILAPP_PORT=<port> -a <appname>


Where <host> is your host and <port> is your papertrailapp port
number, and <appname> is the name of your application.  Then restart
your application

    rhc app restart <appname>

Then install this cartridge

    rhc cartridge-add https://raw.github.com/w-vi/openshift-papertrailapp-cartridge/master/metadata/manifest.yml -a <appname>

This cartridge will monitor the files in all log directories that are published as environment variables, and exist.
You can ssh into your gear and run the following command to see what directories will be monitored

    env | grep LOG

Please log any issues to the git repository issue tracker
