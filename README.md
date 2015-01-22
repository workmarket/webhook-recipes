##Work Market Webhook Recipes

The following webhook recipes are samples to highlight the capabilities of webhooks as a feature.  In most cases, these require some setup on the remote system (typically to enable API access).

Webhooks can be configured here: https://www.workmarket.com/mmw/integration/webhooks


| Dropbox (Upload)             |                                                                         |
|:----------------------|-------------------------------------------------------------------------|
| Description          | Upload new files into a Dropbox folder rootFolder/[assignmentId]/[fileName].  **Note**: you must set up API access for your Dropbox account and get an access token. See here: https://www.dropbox.com/developers |
| Event        | Attachment Added | 
| URL          | https://api-content.dropbox.com/1/files_put/auto/${client_name}/${assignment_id}/${file_name} | 
| Method | PUT |
| Headers | Authorization: Bearer [YOUR_DROPBOX_TOKEN] <br> Content-type: application/octet-stream |
| Body | ${file_data} |


| Dropbox (Delete)             |                                                                         |
|:----------------------|-------------------------------------------------------------------------|
| Description          | Upload new files into a Dropbox folder rootFolder/[assignmentId]/[fileName].  **Note**: you must set up API access for your Dropbox account and get an access token. See here: https://www.dropbox.com/developers |
| Event        | Attachment Removed | 
| URL          | https://api.dropbox.com/1/fileops/delete?root=auto&path=${client_name}/${assignment_id}/${file_name} | 
| Method | POST |
| Headers | Authorization: Bearer [YOUR_DROPBOX_TOKEN] <br> Content-type: application/octet-stream |
| Body | None |



| Hipchat              |                                                                         |
|:----------------------|-------------------------------------------------------------------------|
| Description          | Posts a message to a Hipchat room. **Note**: you must get a Hipchat API token, and must get your room ID.|
| Event        | Note Added (but you could do any number of event types here) | 
| URL          | https://api.hipchat.com/v1/rooms/message
| Method | POST |
| Headers | Content-type: application/x-www-form-urlencoded |
| Body | auth_token=[token]&room_id=[room_id]&from=Webhook&message=${note}&color=purple&message_format=text&notify=0 |


| Twilio SMS              |                                                                         |
|:----------------------|-------------------------------------------------------------------------|
| Description          | Sends an SMS text message via the Twilio API. **Note**: you must have a Twilio account and will need to get your account SID and auth token.|
| Event        | Note Added (but you could do any number of event types here) | 
| URL          | https://[ACCOUNT SID]:[AUTH TOKEN]@api.twilio.com/2010-04-01/Accounts/[ACCOUNT SID]/Messages.json
| Method | POST |
| Headers | Content-type: application/x-www-form-urlencoded |
| Body | To=[TO_PHONE_NUMBER]&From=+[FROM_PHONE_NUMBER]&Body=${note} |
