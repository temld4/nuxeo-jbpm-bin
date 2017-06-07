## Nuxeo JBPM package

### Installation instructions

#### Prerequisities

Let us use the following designations:

`$NUXEO_SERVER_PATH` - full path to Nuxeo Server root folder

`$PACKAGE_PATH` - full path to a folder where you will put Nuxeo JBPM package

`nuxeo-jbpm-package-9.2-SNAPSHOT.zip` - name of the Nuxeo JBPM package

Note: You should have nuxeo-jsf-ui package installed, otherwise you need your Nuxeo Server instance to be registered, so the required package will be automatically installed from Nuxeo Marketplace during JBPM package installation.

#### Installation

1. Download Nuxeo JBPM package (we suppose it to be nuxeo-jbpm-package-9.2-SNAPSHOT.zip, but name can vary)

2. Put it in `$PACKAGE_PATH` folder

3. Execute the following command:

    `$NUXEO_SERVER_PATH/bin/nuxeoctl mp-install $PACKAGE_PATH/nuxeo-jbpm-package-9.2-SNAPSHOT.zip`
    
4. Answer 'yes' to the prompt appearing

5. Add the following configuration to context.xml file located at $NUXEO_SERVER_PATH/conf/ right before closing `</Context>` tag

    ```
    <Resource name="jdbc/nxjbpm" auth="Container" type="javax.sql.DataSource"
              maxActive="100" maxIdle="30" maxWait="10000"
              driverClassName="org.apache.derby.jdbc.EmbeddedDriver"
              url="jdbc:derby:nxjbpm;create=true"/>
    ```

