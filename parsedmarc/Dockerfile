FROM python:3.9-alpine3.16

RUN apk add --update --no-cache libxml2-dev libxslt-dev
RUN apk add --update --no-cache --virtual .build_deps build-base libffi-dev \
    && pip install parsedmarc \
    && apk del .build_deps

ADD crontab /etc/cron.d/parsedmarc-cron
RUN chmod 0644 /etc/cron.d/parsedmarc-cron
RUN touch /var/log/cron.log
CMD cron && tail -f /var/log/cron.log
