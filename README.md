<h2>Configure Greenlight</h2>
<h4>Copy sample.env filr to .env file and you’ll see that it contains information for all of the Greenlight configuration options. Some of these are mandatory.</h4>

Greenlight needs a secret key in order to run in production. To generate this, run:

docker run --rm bigbluebutton/greenlight:v2 bundle exec rake secret
Inside your .env file, set the SECRET_KEY_BASE option to this key. You don’t need to surround it in quotations.

<h4>Setting BigBlueButton CredentialsAnchor link for: setting bigbluebutton credentials
By default, your Greenlight instance will automatically connect to test-install.blindsidenetworks.com if no BigBlueButton credentials are specified. To set Greenlight to connect to your BigBlueButton server (the one it’s installed on), you need to give Greenlight the endpoint and the secret. To get the credentials, run:</h4>

sudo bbb-conf --secret

In your .env file, set the BIGBLUEBUTTON_ENDPOINT to the URL, and set BIGBLUEBUTTON_SECRET to the secret. If in case you are using Scalelite the BIGBLUEBUTTON_ENDPOINT should be like "https://test.example.com/bigbluebutton/api".

<h2>Creating an Administrator Account</h2>
To create an Administrator account with the default values, in the Greenlight directory, run the following command:

docker exec greenlight-v2 bundle exec rake admin:create

<h4>If you would like to configure the name, email, or password of the Administrator account, replace the previous command with this:</h4>

docker exec greenlight-v2 bundle exec rake user:create["name","email","password","admin"]

For creating user. 

docker exec greenlight-v2 bundle exec rake user:create["name","email","password","user"]

