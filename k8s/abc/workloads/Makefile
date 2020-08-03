# will trigger a deploy?

fetch_cert:
	kubeseal --fetch-cert --controller-namespace=kube-system --controller-name=sealed-secrets-controller > pub-cert.pem

gen_secret:
	kubectl create secret generic tfcloudtoken --from-literal=user=admin --from-literal=password=admin --dry-run -o json > tfcloud_token.json

seal_secret:
	kubeseal --format=yaml --cert=pub-cert.pem < tfcloud_token.json > tfcloud_token.yaml

flux_deploy_status:
	kubectl -n flux logs deployment/flux -f

secrets:
	kubectl get secrets

logs:
	kubectl logs sec-w895l
