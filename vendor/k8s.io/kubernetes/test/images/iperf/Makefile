# Copyright 2016 The Kubernetes Authors All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

TAG = e2e
PREFIX = gcr.io/google_containers
IMAGE = iperf

all: push

container: image

image:
	docker build -t $(PREFIX)/${IMAGE} . # Build new image and automatically tag it as latest
	docker tag $(PREFIX)/${IMAGE} $(PREFIX)/${IMAGE}:$(TAG) # Add the version tag to the latest image

push: image
	gcloud docker push $(PREFIX)/${IMAGE} # Push image tagged as latest to repository
	gcloud docker push $(PREFIX)/${IMAGE}:$(TAG) # Push version tagged image to repository (since this image is already pushed it will simply create or update version tag)

clean:
